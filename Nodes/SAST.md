# SAST

Aliases: SAST, kiểm thử bảo mật tĩnh

Type: Security

## Context / Ngữ cảnh

SAST là node bổ sung cho ComputingWiki về phân tích mã nguồn tĩnh để tìm bug hoặc security issue trước runtime.

## Boundary / Ranh giới

### Nó là gì

SAST dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới phân tích mã nguồn tĩnh để tìm bug hoặc security issue trước runtime.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của SAST là hiểu boundary, input/output, state và failure mode riêng của phân tích mã nguồn tĩnh để tìm bug hoặc security issue trước runtime.

## Project Role / Vai trò trong dự án

SAST giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- SAST control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi SAST?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai SAST sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho SAST nếu script nội bộ không xử lý dữ liệu nhạy cảm
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

- SAST
- static analysis security testing
- kiểm thử bảo mật tĩnh
- sast

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
