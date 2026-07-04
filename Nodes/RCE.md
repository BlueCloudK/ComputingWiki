# RCE

Aliases: Remote Code Execution, thực thi mã từ xa

Type: Security

## Context / Ngữ cảnh

RCE xuất hiện khi attacker có thể khiến server, runtime, container hoặc function thực thi code/command do attacker kiểm soát. Đây là nhóm lỗi có impact rất cao vì có thể dẫn tới chiếm server, đọc secret, chạy malware, pivot nội bộ hoặc phá dữ liệu.

## Boundary / Ranh giới

### Nó là gì

RCE là khả năng thực thi mã từ xa trên môi trường nạn nhân. Nó có thể đến từ command injection, unsafe deserialization, template injection, dependency vulnerability, file upload executable, eval/dynamic code, sandbox escape hoặc tool/plugin chạy input không tin cậy.

### Nó không phải là gì

RCE không phải mọi lỗi security nghiêm trọng. SQL injection, XSS, SSRF hoặc path traversal có boundary riêng, dù một số lỗi có thể chain thành RCE. RCE tập trung vào việc attacker chạy code/command trên runtime hoặc host mà họ không được phép điều khiển.

## Core Mechanism / Cơ chế lõi

RCE xảy ra khi input không tin cậy đi vào primitive có khả năng thực thi: shell command, interpreter, template engine, deserializer, plugin loader, script engine, build hook hoặc native library. Nếu sandbox, allowlist, escaping, patching và privilege boundary không đủ, input biến thành code hoặc command thật.

## Project Role / Vai trò trong dự án

RCE là node cần mở khi review endpoint gọi shell, xử lý file upload, deserialize object, render template, chạy plugin, execute code hoặc dùng dependency có CVE. Nó giúp team ưu tiên threat model, patch, sandbox, least privilege, detection và incident response.

## Output / Artifact nên có

- RCE attack surface inventory: command execution, eval, deserialization, template, upload, plugin
- Dependency/CVE review và patch status
- Sandbox/least privilege note: user, container, seccomp/AppArmor, filesystem, network egress
- Test case cho command injection/deserialization/template payload phù hợp ngữ cảnh
- Incident runbook: isolate host/container, rotate secret, collect logs, rebuild image

## Decision Checklist / Câu hỏi kiểm tra

- Code có gọi shell/interpreter với input từ user/file/network không?
- Có dùng deserialization cho dữ liệu không tin cậy không?
- File upload có thể trở thành executable/script/template không?
- Dependency/runtime có CVE RCE chưa được patch không?
- Process chạy quyền gì, có đọc được secret hoặc ghi filesystem nhạy cảm không?
- Container/sandbox có giới hạn network, filesystem và syscall không?
- Có log/detection cho command bất thường, child process hoặc outbound connection không?

## Failure Modes / Cách nó gây lỗi

- Command injection cho phép attacker chạy lệnh hệ điều hành qua input API.
- Unsafe deserialization tạo object/gadget chain thực thi code.
- Template injection cho phép chạy expression hoặc command trong template engine.
- Upload file/script rồi trigger server execute file đó.
- Dependency RCE chưa patch bị scan và khai thác tự động ngoài internet.
- Process có quyền cao làm RCE chuyển thành full host/container compromise.

## Khi nào chưa cần hoặc dễ over-engineer

- Nếu app không có dynamic execution, shell call, plugin, upload executable hoặc deserialization, review RCE có thể nhẹ hơn.
- Không nên tự build sandbox nếu có thể bỏ hẳn nhu cầu chạy code không tin cậy.
- Không nên chỉ vá input validation mà bỏ qua patch dependency và privilege isolation.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Command Injection]] vì command injection là một đường phổ biến dẫn tới RCE.
- [[Unsafe Deserialization]] vì deserialization gadget có thể thực thi code.
- [[File Upload Vulnerability]] vì upload executable/webshell có thể dẫn tới RCE.
- [[Least Privilege]] vì quyền process quyết định impact sau RCE.
- [[Sandbox]] vì chạy code không tin cậy cần boundary thực thi rõ.

## Liên quan rộng

- Application security
- Incident response
- Dependency vulnerability
- Container hardening

## Keywords / Từ khóa tìm kiếm

- RCE
- Remote Code Execution
- thực thi mã từ xa
- arbitrary code execution
- command execution
- command injection
- unsafe deserialization
- template injection
- sandbox escape
- webshell
- dependency RCE
- CVE RCE
- code execution vulnerability
- remote exploit
- RCE testing

## Source trace

- OWASP Testing Guide
- OWASP Deserialization Cheat Sheet
