# Encryption at Rest

Aliases: Encryption at Rest, encryption at rest, data at rest encryption, mã hóa khi lưu

Type: Security

## Context / Ngữ cảnh

Encryption at Rest là node bổ sung cho ComputingWiki về mã hóa dữ liệu khi lưu trên disk, database hoặc object storage.

## Boundary / Ranh giới

### Nó là gì

Encryption at Rest dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới mã hóa dữ liệu khi lưu trên disk, database hoặc object storage.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Encryption at Rest là hiểu boundary, input/output, state và failure mode riêng của mã hóa dữ liệu khi lưu trên disk, database hoặc object storage.

## Project Role / Vai trò trong dự án

Encryption at Rest giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Encryption at Rest control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Encryption at Rest?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Encryption at Rest sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Encryption at Rest nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Key Management]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Encryption at Rest

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Encryption at Rest
- encryption at rest
- data at rest encryption
- mã hóa khi lưu
- encryption
- rest

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
