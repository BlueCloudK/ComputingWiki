# Zero Trust

Aliases: Zero Trust, zero trust, never trust always verify, không tin mặc định

Type: Security

## Context / Ngữ cảnh

Zero Trust là node bổ sung cho ComputingWiki về mô hình không mặc định tin network/internal actor mà kiểm tra identity/context liên tục.

## Boundary / Ranh giới

### Nó là gì

Zero Trust dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới mô hình không mặc định tin network/internal actor mà kiểm tra identity/context liên tục.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Security; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Zero Trust là hiểu boundary, input/output, state và failure mode riêng của mô hình không mặc định tin network/internal actor mà kiểm tra identity/context liên tục.

## Project Role / Vai trò trong dự án

Zero Trust giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Zero Trust control note hoặc checklist
- Test/security review cho attack path liên quan
- Log/audit hoặc monitoring nếu control fail

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào được bảo vệ bởi Zero Trust?
- Attack path chính là input, auth, session, dependency hay deployment?
- Control có enforce ở backend/runtime đúng chỗ không?

## Failure Modes / Cách nó gây lỗi

- Triển khai Zero Trust sai boundary làm control không chặn được attack path
- Thiếu test/audit làm lỗ hổng chỉ phát hiện sau incident
- Control quá rộng làm false sense of security

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony lớn cho Zero Trust nếu script nội bộ không xử lý dữ liệu nhạy cảm
- Dễ over-engineer nếu thêm nhiều control không map với asset/attack surface

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Least Privilege]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Zero Trust

## Liên quan rộng

- Application security
- Threat modeling
- Secure operation

## Keywords / Từ khóa tìm kiếm

- Zero Trust
- zero trust
- never trust always verify
- không tin mặc định
- zero
- trust

## Source trace

- OWASP Cheat Sheet Series
- OWASP Top 10
- NIST Secure Software Development Framework
