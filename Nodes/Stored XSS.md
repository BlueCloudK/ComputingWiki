# Stored XSS

Aliases: Stored XSS, stored XSS, persistent XSS, XSS lưu trữ

Type: Security

## Context / Ngữ cảnh

Stored XSS là node bổ sung cho ComputingWiki về XSS xảy ra khi payload độc hại được lưu rồi hiển thị cho user khác.

## Boundary / Ranh giới

### Nó là gì

Stored XSS dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới XSS xảy ra khi payload độc hại được lưu rồi hiển thị cho user khác.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Stored XSS là hiểu boundary, input/output, state và failure mode riêng của XSS xảy ra khi payload độc hại được lưu rồi hiển thị cho user khác.

## Project Role / Vai trò trong dự án

Stored XSS giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Stored XSS control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Stored XSS?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Stored XSS sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Stored XSS nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[XSS]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Stored XSS
- [[Output Encoding]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Stored XSS

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Stored XSS
- stored XSS
- persistent XSS
- XSS lưu trữ
- stored

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
