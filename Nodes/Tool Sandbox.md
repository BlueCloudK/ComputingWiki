# Tool Sandbox

Aliases: Tool Sandbox, tool execution sandbox

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Tool Sandbox xuất hiện khi AI agent có thể chạy code, shell, browser, file operation hoặc API action và cần giới hạn môi trường thực thi để giảm rủi ro.

## Boundary / Ranh giới

### Nó là gì

Tool Sandbox là môi trường hoặc policy cô lập tool execution, giới hạn filesystem, network, credential, timeout, CPU/memory và side effect mà tool được phép tạo.

### Nó không phải là gì

Tool Sandbox không phải permission đầy đủ nếu chỉ chạy trong container nhưng vẫn có credential rộng hoặc network mở. Sandbox cần đi cùng tool permission, audit và resource limit.

## Core Mechanism / Cơ chế lõi

Tool call được đưa vào runner cô lập. Runner mount scope tối thiểu, inject credential cần thiết, giới hạn network/resource/time, validate output và ghi trace. Nếu tool vượt policy, sandbox deny hoặc kill execution.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế agent tool runner, code execution, browser automation, file access, tenant isolation hoặc debug vì sao tool bị deny/timeout.

## Output / Artifact nên có

- Sandbox boundary: filesystem/network/process
- Allowed credential/resource scope
- Timeout and resource limits
- Deny/kill behavior
- Audit log and artifact retention rule

## Decision Checklist / Câu hỏi kiểm tra

- Tool được đọc/ghi vùng file nào?
- Network outbound có cần mở không?
- Credential nào được inject và scope ra sao?
- Timeout/CPU/memory limit là bao nhiêu?
- Output/artifact có thể chứa secret không?

## Failure Modes / Cách nó gây lỗi

- Sandbox có network/credential quá rộng.
- Tool write vượt workspace và sửa dữ liệu không mong muốn.
- Không giới hạn timeout/resource làm runner treo.
- Log/artifact leak secret từ sandbox.
- Sandbox cô lập quá mạnh làm tool cần thiết không chạy được nhưng lỗi mơ hồ.

## Khi nào chưa cần hoặc dễ over-engineer

- Chatbot không có tool side effect có thể chưa cần sandbox phức tạp.
- Không nên cho tool write action khi read-only sandbox và audit chưa ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Tool Use]] vì sandbox kiểm soát nơi tool chạy.
- [[Tool Permission]] vì sandbox là enforcement layer sau permission decision.
- [[Least Privilege]] vì sandbox nên cấp scope tối thiểu.
- [[Resource Exhaustion]] vì sandbox cần giới hạn CPU/memory/time.

## Liên quan rộng

- Code execution
- Isolation
- Agent runtime security

## Keywords / Từ khóa tìm kiếm

- Tool Sandbox
- tool execution sandbox
- agent sandbox
- code execution sandbox
- filesystem scope
- network isolation
- tool sandbox debugging

## Source trace

- OpenAI documentation
- OWASP LLM guidance
