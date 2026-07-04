# Authentication

Aliases: identity verification, xác thực, authn, login verification, xác thực người dùng

Type: Security

## Context / Ngữ cảnh

Authentication xuất hiện khi hệ thống cần biết một actor là ai trước khi cho tạo session, cấp token, truy cập account hoặc thực hiện hành động nhạy cảm. Actor có thể là user, service account, API client, device hoặc workload nội bộ.

## Boundary / Ranh giới

### Nó là gì

Authentication là quá trình xác minh identity: user/client có chứng minh được họ là danh tính họ khai báo không. Cơ chế có thể là password, passkey, OTP/MFA, OAuth/OIDC login, client certificate, API key, signed token hoặc service identity.

### Nó không phải là gì

Authentication không quyết định actor được làm gì sau khi đăng nhập. Đó là Authorization. Một user xác thực thành công vẫn có thể không được xem/sửa resource cụ thể. Authentication cũng không phải validation input; nó tập trung vào chứng minh identity và quản lý session/token sau xác thực.

## Core Mechanism / Cơ chế lõi

Flow thường gồm nhận credential/assertion, verify với identity store/provider, kiểm tra MFA/risk nếu cần, tạo session/token, set cookie/header, rồi audit login. Security phụ thuộc vào credential storage, token/session lifecycle, MFA, rate limit, account recovery, logout/revoke và chống session hijacking.

## Project Role / Vai trò trong dự án

Authentication ảnh hưởng tới login UX, session architecture, security boundary và audit. Khi thiết kế backend, team phải quyết định identity provider nào tin, session/token lưu ở đâu, login failure trả lỗi thế nào, account recovery ra sao, và token/cookie có thể bị đánh cắp/thu hồi thế nào.

## Output / Artifact nên có

- Auth flow diagram: login, MFA, refresh, logout, password reset/account recovery
- Credential/session policy: hash password, token lifetime, cookie flags, rotation/revoke
- Identity source: local user DB, OIDC provider, SSO, service account hoặc API key
- Security test case: brute force, expired token, stolen token, disabled user, session fixation
- Audit log: login success/failure, MFA failure, password reset, suspicious login

## Decision Checklist / Câu hỏi kiểm tra

- Actor là user, service, device hay third-party client?
- Credential nào được dùng và lưu/verify ở đâu?
- Session/token có lifetime, refresh, revoke và logout rõ không?
- Cookie/token có HttpOnly, Secure, SameSite hoặc storage boundary đúng không?
- Có MFA/passkey/risk check cho account nhạy cảm không?
- Login failure có rate limit và message không leak user enumeration không?
- Account recovery có yếu hơn login chính không?

## Failure Modes / Cách nó gây lỗi

- Password lưu/hash yếu làm credential leak thành account takeover.
- Token/session không expire hoặc không revoke được khi user logout/disable.
- Login failure message làm attacker enumerate email/user tồn tại.
- Thiếu rate limit/lockout làm brute force hoặc credential stuffing dễ hơn.
- Token lưu ở nơi dễ bị XSS lấy cắp.
- Account recovery/password reset yếu hơn login chính và trở thành đường chiếm tài khoản.
- Nhầm authentication với authorization, chỉ cần login là xem được resource người khác.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype nội bộ không có dữ liệu nhạy có thể dùng provider có sẵn thay vì tự build auth đầy đủ.
- Không nên tự implement password/session crypto nếu framework/provider uy tín đã có.
- Không nên thêm quá nhiều auth flow khi chưa có threat model và UX rõ.

## Gồm những gì

- [[Authorization]]
- [[Secret]]

## Nối mạnh

- [[Authorization]] vì authentication xác định actor, còn authorization quyết định actor được làm gì.
- [[Session Management]] vì login thường tạo session hoặc token lifecycle.
- [[OAuth2]] vì OAuth2/OIDC thường nằm trong flow đăng nhập/ủy quyền hiện đại.
- [[OpenID Connect]] vì OIDC là identity layer phổ biến cho authentication.
- [[Cookie]] vì web session thường được lưu bằng cookie có security flags.

## Liên quan rộng

- Application security
- Identity provider
- Account recovery
- Audit logging

## Keywords / Từ khóa tìm kiếm

- Authentication
- authn
- identity verification
- xác thực
- xác thực người dùng
- login verification
- password login
- token authentication
- session authentication
- MFA
- passkey
- credential stuffing
- account recovery
- login audit
- session hijacking

## Source trace

- OWASP Authentication Cheat Sheet
