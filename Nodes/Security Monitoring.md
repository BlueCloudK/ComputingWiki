# Security Monitoring

Aliases: Security Monitoring, security monitoring, security alert, giám sát bảo mật

Type: Security

## Context / Ngữ cảnh

Security Monitoring là node bổ sung cho ComputingWiki về theo dõi signal bảo mật để phát hiện misuse, intrusion hoặc control failure.

## Boundary / Ranh giới

### Nó là gì

Security Monitoring dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới theo dõi signal bảo mật để phát hiện misuse, intrusion hoặc control failure.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Security Monitoring là hiểu boundary, input/output, state và failure mode riêng của theo dõi signal bảo mật để phát hiện misuse, intrusion hoặc control failure.

## Project Role / Vai trò trong dự án

Security Monitoring giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Security Monitoring control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Security Monitoring?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Security Monitoring sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Security Monitoring nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Monitoring]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Security Monitoring
- [[Incident Response]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Security Monitoring

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Security Monitoring
- security monitoring
- security alert
- giám sát bảo mật
- security
- monitoring

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
