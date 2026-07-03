# DAST

Aliases: DAST, kiểm thử bảo mật động

Type: Security

## Context / Ngữ cảnh

DAST là node bổ sung cho ComputingWiki về kiểm thử bảo mật động trên app đang chạy.

## Boundary / Ranh giới

### Nó là gì

DAST dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới kiểm thử bảo mật động trên app đang chạy.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của DAST là hiểu boundary, input/output, state và failure mode riêng của kiểm thử bảo mật động trên app đang chạy.

## Project Role / Vai trò trong dự án

DAST giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- DAST control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi DAST?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai DAST sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho DAST nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh


- Chưa có nối mạnh ngoài các node con trực tiếp
## Liên quan rộng

- Security
- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- DAST
- dynamic application security testing
- kiểm thử bảo mật động
- dast

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
