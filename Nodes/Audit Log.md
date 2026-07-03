# Audit Log

Aliases: Audit Log, audit log, security audit log, log kiểm toán

Type: Security

## Context / Ngữ cảnh

Audit Log là node bổ sung cho ComputingWiki về log ghi lại hành động nhạy cảm để điều tra và chứng minh accountability.

## Boundary / Ranh giới

### Nó là gì

Audit Log dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới log ghi lại hành động nhạy cảm để điều tra và chứng minh accountability.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Audit Log là hiểu boundary, input/output, state và failure mode riêng của log ghi lại hành động nhạy cảm để điều tra và chứng minh accountability.

## Project Role / Vai trò trong dự án

Audit Log giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Audit Log control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Audit Log?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Audit Log sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Audit Log nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Logging]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Audit Log
- [[Security Monitoring]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Audit Log

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Audit Log
- audit log
- security audit log
- log kiểm toán
- audit

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
