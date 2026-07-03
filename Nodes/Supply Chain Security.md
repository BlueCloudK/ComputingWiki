# Supply Chain Security

Aliases: Supply Chain Security, supply chain security, software supply chain, bảo mật chuỗi cung ứng

Type: Security

## Context / Ngữ cảnh

Supply Chain Security là node bổ sung cho ComputingWiki về bảo vệ dependency, build, artifact và release pipeline khỏi bị chèn độc.

## Boundary / Ranh giới

### Nó là gì

Supply Chain Security dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới bảo vệ dependency, build, artifact và release pipeline khỏi bị chèn độc.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Supply Chain Security là hiểu boundary, input/output, state và failure mode riêng của bảo vệ dependency, build, artifact và release pipeline khỏi bị chèn độc.

## Project Role / Vai trò trong dự án

Supply Chain Security giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Supply Chain Security control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Supply Chain Security?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Supply Chain Security sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Supply Chain Security nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dependency Scanning]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Supply Chain Security
- [[SBOM]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Supply Chain Security

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Supply Chain Security
- supply chain security
- software supply chain
- bảo mật chuỗi cung ứng
- supply
- chain
- security

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
