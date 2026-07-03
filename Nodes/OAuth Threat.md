# OAuth Threat

Aliases: OAuth Threat, OAuth threat, OAuth attack, rủi ro OAuth

Type: Security

## Context / Ngữ cảnh

OAuth Threat là node bổ sung cho ComputingWiki về nhóm rủi ro trong OAuth như redirect URI abuse, token leak và consent phishing.

## Boundary / Ranh giới

### Nó là gì

OAuth Threat dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới nhóm rủi ro trong OAuth như redirect URI abuse, token leak và consent phishing.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của OAuth Threat là hiểu boundary, input/output, state và failure mode riêng của nhóm rủi ro trong OAuth như redirect URI abuse, token leak và consent phishing.

## Project Role / Vai trò trong dự án

OAuth Threat giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- OAuth Threat control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi OAuth Threat?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai OAuth Threat sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho OAuth Threat nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[OAuth2]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng OAuth Threat
- [[API Security]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng OAuth Threat

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- OAuth Threat
- OAuth threat
- OAuth attack
- rủi ro OAuth
- oauth
- threat

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
