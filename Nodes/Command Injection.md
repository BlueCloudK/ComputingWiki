# Command Injection

Aliases: Command Injection, command injection, OS command injection, chèn lệnh hệ điều hành

Type: Security

## Context / Ngữ cảnh

Command Injection là node bổ sung cho ComputingWiki về lỗ hổng cho phép attacker chèn lệnh OS vào command mà app thực thi.

## Boundary / Ranh giới

### Nó là gì

Command Injection dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới lỗ hổng cho phép attacker chèn lệnh OS vào command mà app thực thi.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Command Injection là hiểu boundary, input/output, state và failure mode riêng của lỗ hổng cho phép attacker chèn lệnh OS vào command mà app thực thi.

## Project Role / Vai trò trong dự án

Command Injection giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Command Injection control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Command Injection?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Command Injection sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Command Injection nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Input Validation]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Command Injection

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Command Injection
- command injection
- OS command injection
- chèn lệnh hệ điều hành
- command
- injection

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
