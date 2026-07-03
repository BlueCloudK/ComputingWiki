# Output Encoding

Aliases: output escaping, mã hóa output

Type: Security

## Context / Ngữ cảnh

Output Encoding xuất hiện khi dữ liệu untrusted được đưa vào HTML, JS, URL hoặc interpreter context khác.

## Boundary / Ranh giới

### Nó là gì

Output Encoding là encode dữ liệu theo context đích để nó được hiểu là data chứ không thành code.

### Nó không phải là gì

Nó không phải input validation và encoding sai context vẫn nguy hiểm.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chọn encoder theo sink: HTML body, attribute, JavaScript, URL, CSS hoặc command context.

## Project Role / Vai trò trong dự án

Node này giúp phòng XSS và injection ở output boundary.

## Output / Artifact nên có

- Encoding matrix theo sink: HTML, attribute, JS, URL
- Template/framework auto-escape note
- XSS test payload cho output boundary

## Decision Checklist / Câu hỏi kiểm tra

- Output đi vào context nào?
- Framework có auto-escape context đó không?
- Có sink nào dùng dangerouslySetInnerHTML/raw HTML không?

## Failure Modes / Cách nó gây lỗi

- Encode sai context vẫn XSS
- Tin input validation rồi bỏ output encoding
- Double encode làm UI/data hỏng

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không render untrusted data
- Dễ over-engineer nếu encode mọi nơi mà không biết sink context

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[XSS]] vì output encoding là control chính chống XSS
- [[Input Validation]] vì validation và encoding bổ trợ nhau

## Liên quan rộng

- Escaping
- Template security

## Keywords / Từ khóa tìm kiếm

- Output Encoding
- HTML encoding
- contextual encoding
- XSS prevention
- escape output
- encode user input
- mã hóa output chống XSS

## Source trace

- OWASP XSS Prevention Cheat Sheet
