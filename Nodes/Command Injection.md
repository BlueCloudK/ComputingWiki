# Command Injection

Aliases: Command Injection, command injection, OS command injection, chèn lệnh hệ điều hành

Type: Security

## Context / Ngữ cảnh

Command Injection xuất hiện khi application tạo OS command từ input không tin cậy rồi chạy qua shell hoặc process execution API. Nó thường gặp trong feature convert file, gọi binary như `ffmpeg`, backup script, ping/traceroute tool, image processing, CI/deploy hook hoặc admin utility.

## Boundary / Ranh giới

### Nó là gì

Command Injection là lỗi cho phép attacker chèn thêm command/argument/control operator vào lệnh hệ điều hành mà app thực thi. Nếu process có quyền cao, lỗi này có thể dẫn tới RCE, đọc secret, ghi file, mở reverse shell hoặc phá dữ liệu.

### Nó không phải là gì

Command Injection không phải mọi lỗi input validation. Nếu input đi vào SQL thì là SQL injection; nếu đi vào template/deserialization/file path thì có boundary khác. Command Injection tập trung vào execution primitive như shell, subprocess, `system`, `exec`, `spawn`, script runner hoặc external binary.

## Core Mechanism / Cơ chế lõi

App nối chuỗi command từ input rồi đưa vào shell. Shell parse ký tự như `;`, `&&`, `|`, `$()`, backtick, redirect hoặc whitespace thành lệnh/argument mới. Cách an toàn hơn là tránh shell, dùng API truyền argument array, allowlist command/argument, validate type/range và chạy process với least privilege/sandbox.

## Project Role / Vai trò trong dự án

Command Injection là node cần mở khi code gọi command line tool, chạy script, xử lý file upload bằng binary ngoài, hoặc agent/tool có quyền shell. Nó giúp team review chỗ nào input chạm execution, user nào điều khiển argument và process chạy với quyền gì.

## Output / Artifact nên có

- Command execution inventory: nơi nào gọi shell/binary/script
- Safe execution rule: no shell string, argument array, allowlist, fixed executable path
- Input validation cho argument: enum, numeric range, filename id, không raw command
- Least privilege/sandbox note: user, container, filesystem, network, timeout
- Test case cho shell metacharacter, whitespace, encoded payload và unexpected argument

## Decision Checklist / Câu hỏi kiểm tra

- Code có gọi shell/process với input từ user/file/network không?
- Có dùng shell string hay argument array?
- Executable path và allowed arguments có cố định/allowlist không?
- Input có thể chứa `;`, `&&`, `|`, `$()`, backtick, newline hoặc redirect không?
- Process chạy user/quyền nào và đọc được secret/file gì?
- Có timeout, resource limit và output size limit không?
- Có audit log cho command execution nhạy cảm không?

## Failure Modes / Cách nó gây lỗi

- Nối chuỗi `ping ` + user input làm attacker thêm `; cat /etc/passwd`.
- Escape/quote thủ công thiếu case encoding/newline/argument injection.
- Cho user chọn executable/subcommand quá rộng thành arbitrary command.
- Process chạy cùng quyền app và đọc được env secret/API key.
- Output command được trả thẳng cho user làm lộ filesystem/internal detail.
- Tool/agent có shell access không allowlist, prompt/input gián tiếp dẫn tới command execution.

## Khi nào chưa cần hoặc dễ over-engineer

- Nếu feature không gọi OS command/script/binary thì risk này thấp hơn.
- Không nên chạy shell nếu có library API làm cùng việc an toàn hơn.
- Không nên tự viết escaping phức tạp nếu có thể bỏ shell và truyền argument array.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Input Validation]] vì command argument từ input không tin cậy cần validate rất chặt.
- [[RCE]] vì command injection thường dẫn trực tiếp tới remote code execution.
- [[Least Privilege]] vì quyền process quyết định impact khi command injection xảy ra.
- [[Sandbox]] vì chạy binary/tool không tin cậy cần boundary thực thi.
- [[Secret]] vì command injection có thể đọc env secret hoặc file credential.

## Liên quan rộng

- Application security
- Secure coding
- Agent/tool safety
- Runtime sandboxing

## Keywords / Từ khóa tìm kiếm

- Command Injection
- command injection
- OS command injection
- chèn lệnh hệ điều hành
- shell injection
- argument injection
- subprocess security
- exec system spawn
- shell metacharacters
- command execution vulnerability
- no shell argument array
- command injection testing
- command injection debugging

## Source trace

- OWASP Command Injection
- OWASP Input Validation Cheat Sheet
