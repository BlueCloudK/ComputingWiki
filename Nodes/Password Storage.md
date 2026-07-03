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

- Password hashing policy: algorithm, salt, cost
- Migration plan cho hash cũ
- Pepper/secret handling nếu dùng

## Decision Checklist / Câu hỏi kiểm tra

- Có dùng Argon2/bcrypt/scrypt thay vì hash nhanh không?
- Cost factor có phù hợp server và threat không?
- Password reset/change có invalidate session cần thiết không?

## Failure Modes / Cách nó gây lỗi

- Lưu plaintext hoặc SHA trực tiếp
- Salt/pepper xử lý sai làm giảm bảo vệ
- Không nâng cấp hash cost theo thời gian

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu dùng identity provider không tự lưu password
- Dễ over-engineer nếu tự xây auth khi provider chuẩn đủ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authentication]] vì password verifier phục vụ authentication
- [[Secret]] vì pepper/key liên quan secret handling

## Liên quan rộng

- Credential security

## Keywords / Từ khóa tìm kiếm

- Password Storage
- password hashing
- salt
- bcrypt
- argon2
- password database
- lưu mật khẩu an toàn

## Source trace

- OWASP Password Storage Cheat Sheet
