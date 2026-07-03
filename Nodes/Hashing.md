# Hashing

Aliases: Hashing, hashing, hash function, hàm băm

Type: Security

## Context / Ngữ cảnh

Hashing là node bổ sung cho ComputingWiki về biến input thành digest một chiều dùng cho integrity hoặc password storage.

## Boundary / Ranh giới

### Nó là gì

Hashing dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới biến input thành digest một chiều dùng cho integrity hoặc password storage.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Hashing là hiểu boundary, input/output, state và failure mode riêng của biến input thành digest một chiều dùng cho integrity hoặc password storage.

## Project Role / Vai trò trong dự án

Hashing giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Hashing control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Hashing?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Hashing sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Hashing nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Password Storage]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Hashing

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Hashing
- hashing
- hash function
- hàm băm

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
