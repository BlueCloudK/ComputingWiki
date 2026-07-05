# Session Management

Aliases: session security, quản lý phiên

Type: Security

## Context / Ngữ cảnh

Session Management xuất hiện khi hệ thống cần duy trì trạng thái đăng nhập hoặc phiên làm việc sau authentication. Nó quyết định session/token được tạo, lưu, truyền, expire, rotate, revoke và bảo vệ như thế nào trong browser, mobile app, backend hoặc service-to-service flow.

## Boundary / Ranh giới

### Nó là gì

Session Management là practice quản lý lifecycle của session identifier, cookie, access token, refresh token hoặc server-side session. Mục tiêu là giữ user/service đã xác thực trong phiên hợp lệ nhưng giảm rủi ro session hijacking, fixation, replay và token leak.

### Nó không phải là gì

Session Management không phải authentication bản thân và không thay thế authorization. Authentication xác minh identity; session giữ identity đó qua nhiều request; authorization vẫn phải kiểm tra quyền trên từng action/resource. Session cũng không nên là nơi lưu toàn bộ state nghiệp vụ lớn nếu có storage/domain model phù hợp hơn.

## Core Mechanism / Cơ chế lõi

Sau login, hệ thống tạo session id/token đủ ngẫu nhiên, gắn với user/device/scope, truyền qua cookie/header an toàn, đặt expiry, rotate khi privilege đổi hoặc refresh, revoke khi logout/password change/compromise, và kiểm tra session ở mỗi request. Với browser, cookie flags như HttpOnly, Secure, SameSite rất quan trọng.

## Project Role / Vai trò trong dự án

Session Management là node cần mở khi thiết kế login/logout, refresh token, remember-me, password reset, multi-device session, admin revoke, hoặc debug user vẫn đăng nhập sau logout. Nó giúp team phân biệt cookie/session/token storage với auth/permission logic.

## Output / Artifact nên có

- Session/token lifecycle policy: create, rotate, expire, refresh, revoke
- Storage rule: cookie, server-side store, Authorization header, mobile secure storage
- Cookie/token security config: HttpOnly, Secure, SameSite, domain/path, TTL
- Logout/revoke behavior: single device, all devices, password change, account disable
- Test case cho fixation, expired token, stolen token, refresh replay và logout invalidation

## Decision Checklist / Câu hỏi kiểm tra

- Session id/token được tạo với entropy đủ mạnh chưa?
- Token/session lưu ở đâu và có bị JavaScript/log đọc được không?
- Cookie có HttpOnly, Secure, SameSite, domain/path đúng không?
- Access token và refresh token có lifetime khác nhau không?
- Logout/password change/account disable có revoke session cũ không?
- Session có rotate sau login hoặc privilege escalation không?
- Có detect/revoke khi token bị nghi ngờ lộ không?

## Failure Modes / Cách nó gây lỗi

- Session fixation: attacker ép victim dùng session id đã biết trước.
- Session hijacking do token/cookie bị lộ qua XSS, log, HTTP hoặc localStorage.
- Session không expire hoặc refresh token không revoke được.
- Logout chỉ xóa client cookie nhưng server-side session/token vẫn hợp lệ.
- SameSite/domain/path sai làm cookie không gửi hoặc gửi quá rộng.
- Refresh token replay cho phép attacker giữ quyền lâu sau khi access token hết hạn.

## Khi nào chưa cần hoặc dễ over-engineer

- App không có login/session thì không cần session management.
- Script nội bộ ngắn hạn có thể dùng token đơn giản nhưng vẫn phải tránh log/lộ secret.
- Không nên tự build session/token framework nếu platform/provider đã có implementation chuẩn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authentication]] vì session bắt đầu sau khi xác thực thành công.
- [[Cookie]] vì browser session thường dựa vào cookie và cookie flags.
- [[Transport Layer Protection]] vì session token cần truyền qua kênh bảo mật.
- [[Secret]] vì token/session id là secret bearer credential.
- [[Authorization]] vì session identity vẫn cần quyền đúng trên từng resource.

## Liên quan rộng

- Cookies
- Token lifecycle
- Account security
- Browser security

## Keywords / Từ khóa tìm kiếm

- Session Management
- session security
- quản lý phiên
- user session
- session cookie
- session timeout
- session fixation
- session hijacking
- logout invalidation
- refresh token rotation
- token revocation
- HttpOnly cookie
- SameSite cookie
- session management debugging

## Source trace

- OWASP Session Management Cheat Sheet
