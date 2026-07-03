# DOM XSS

Aliases: DOM XSS, client-side XSS, XSS trên DOM

Type: Security

## Context / Ngữ cảnh

DOM XSS là node bổ sung cho ComputingWiki về XSS xảy ra trong client-side JavaScript khi DOM sink nhận dữ liệu không an toàn.

## Boundary / Ranh giới

### Nó là gì

DOM XSS dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới XSS xảy ra trong client-side JavaScript khi DOM sink nhận dữ liệu không an toàn.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của DOM XSS là hiểu boundary, input/output, state và failure mode riêng của XSS xảy ra trong client-side JavaScript khi DOM sink nhận dữ liệu không an toàn.

## Project Role / Vai trò trong dự án

DOM XSS giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- DOM XSS control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi DOM XSS?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai DOM XSS sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho DOM XSS nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[XSS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng DOM XSS
- [[DOM]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng DOM XSS

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- DOM XSS
- client-side XSS
- XSS trên DOM

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
