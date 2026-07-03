# Password Storage

Aliases: password hashing, lưu mật khẩu

Type: Security

## Context / Ngữ cảnh

Password Storage xuất hiện khi hệ thống phải lưu verifier mật khẩu mà không được lưu plaintext.

## Boundary / Ranh giới

### Nó là gì

Password Storage là practice hash password bằng thuật toán chuyên dụng, salt và cost phù hợp.

### Nó không phải là gì

Nó không phải encryption thông thường và không thay thế MFA/session security.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là dùng one-way password hashing chậm như Argon2, bcrypt hoặc scrypt để giảm impact khi database leak.

## Project Role / Vai trò trong dự án

Node này giúp bảo vệ user khi credential store bị lộ.

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

- [[Authentication]] vì password verifier phục vụ authentication
- [[Secret]] vì pepper/key liên quan secret handling

## Liên quan rộng

- Credential security

## Source trace

- OWASP Password Storage Cheat Sheet
