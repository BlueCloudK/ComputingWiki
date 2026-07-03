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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[XSS]] vì output encoding là control chính chống XSS
- [[Input Validation]] vì validation và encoding bổ trợ nhau

## Liên quan rộng

- Escaping
- Template security

## Source trace

- OWASP XSS Prevention Cheat Sheet
