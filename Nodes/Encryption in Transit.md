# Encryption in Transit

Aliases: Encryption in Transit, encryption in transit, TLS encryption, mã hóa khi truyền

Type: Security

## Context / Ngữ cảnh

Encryption in Transit là node bổ sung cho ComputingWiki về mã hóa dữ liệu khi truyền qua network.

## Boundary / Ranh giới

### Nó là gì

Encryption in Transit dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới mã hóa dữ liệu khi truyền qua network.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Encryption in Transit là hiểu boundary, input/output, state và failure mode riêng của mã hóa dữ liệu khi truyền qua network.

## Project Role / Vai trò trong dự án

Encryption in Transit giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Encryption in Transit control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Encryption in Transit?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Encryption in Transit sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Encryption in Transit nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[TLS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Encryption in Transit
- [[HTTPS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Encryption in Transit

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Encryption in Transit
- encryption in transit
- TLS encryption
- mã hóa khi truyền
- encryption
- transit

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
