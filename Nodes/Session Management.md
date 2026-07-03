# Session Management

Aliases: session security, quản lý phiên

Type: Security

## Context / Ngữ cảnh

Session Management xuất hiện khi hệ thống cần duy trì trạng thái đăng nhập hoặc phiên làm việc an toàn.

## Boundary / Ranh giới

### Nó là gì

Session Management là practice tạo, lưu, rotate, expire và bảo vệ session/token sau authentication.

### Nó không phải là gì

Nó không phải authentication bản thân và không thay thế authorization.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là session identifier/token đủ ngẫu nhiên, truyền/lưu an toàn, expire đúng và revoke khi cần.

## Project Role / Vai trò trong dự án

Node này giúp tránh session hijacking, fixation và logout không hiệu lực.

## Output / Artifact nên có

- Session/token lifecycle policy
- Cookie flags hoặc token storage rule
- Logout/revoke/expiry behavior

## Decision Checklist / Câu hỏi kiểm tra

- Session id/token được tạo và rotate thế nào?
- Cookie có HttpOnly/Secure/SameSite không?
- Logout/password change có revoke session cũ không?

## Failure Modes / Cách nó gây lỗi

- Session fixation/hijacking
- Token lưu local/log không an toàn
- Session không expire hoặc không revoke được

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu app không có login/session
- Dễ over-engineer nếu script nội bộ ít rủi ro bị ép session framework nặng

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authentication]] vì session bắt đầu sau khi xác thực
- [[Transport Layer Protection]] vì session token cần truyền qua kênh bảo mật

## Liên quan rộng

- Cookies
- Token lifecycle

## Keywords / Từ khóa tìm kiếm

- Session Management
- session security
- quản lý phiên
- session
- management
- Security
- bảo mật phần mềm

## Source trace

- OWASP Session Management Cheat Sheet
