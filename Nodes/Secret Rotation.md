# Secret Rotation

Aliases: Secret Rotation, secret rotation, rotate secret, xoay vòng secret

Type: Security

## Context / Ngữ cảnh

Secret Rotation là node bổ sung cho ComputingWiki về quy trình thay secret/key định kỳ hoặc khi nghi lộ.

## Boundary / Ranh giới

### Nó là gì

Secret Rotation dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới quy trình thay secret/key định kỳ hoặc khi nghi lộ.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Secret Rotation là hiểu boundary, input/output, state và failure mode riêng của quy trình thay secret/key định kỳ hoặc khi nghi lộ.

## Project Role / Vai trò trong dự án

Secret Rotation giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Secret Rotation control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Secret Rotation?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Secret Rotation sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Secret Rotation nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Secret]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Secret Rotation
- [[Key Management]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Secret Rotation

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Secret Rotation
- secret rotation
- rotate secret
- xoay vòng secret
- secret
- rotation

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
