# OAuth2

Aliases: OAuth2, OAuth 2.0, ủy quyền OAuth

Type: Backend Engineering

## Context / Ngữ cảnh

OAuth2 xuất hiện khi một application cần truy cập tài nguyên ở resource server thay mặt user hoặc client mà không nhận trực tiếp password của user. Nó thường gặp trong login with provider, third-party API integration, mobile/web app authorization, service integration và delegated access.

## Boundary / Ranh giới

### Nó là gì

OAuth2 là authorization framework để cấp access token cho client sau một flow được kiểm soát giữa client, authorization server, resource owner và resource server. Nó trả lời câu hỏi “client này được phép truy cập tài nguyên nào, trong scope nào, trong bao lâu”.

### Nó không phải là gì

OAuth2 không phải authentication layer đầy đủ cho user identity. Nếu cần đăng nhập và xác minh danh tính user, thường cần OpenID Connect trên OAuth2. OAuth2 cũng không tự đảm bảo app an toàn nếu redirect URI, scope, token storage, PKCE hoặc client secret bị cấu hình sai.

## Core Mechanism / Cơ chế lõi

OAuth2 hoạt động qua flow như authorization code + PKCE, client credentials hoặc refresh token. Client xin authorization, nhận authorization code/token qua authorization server, rồi dùng access token gọi resource server. Security phụ thuộc vào redirect URI validation, scope, token lifetime, PKCE, client authentication và cách token được lưu/refresh/revoke.

## Project Role / Vai trò trong dự án

OAuth2 ảnh hưởng tới login integration, third-party API access, token lifecycle, permission scope và backend security boundary. Khi thiết kế hệ thống, team phải quyết định flow nào dùng cho web/mobile/service, token được lưu ở đâu, scope nào tối thiểu, refresh/revoke thế nào và API nào verify token ở đâu.

## Output / Artifact nên có

- OAuth2 flow decision: authorization code + PKCE, client credentials, device flow hoặc refresh token
- Client registration note: client id, redirect URI, allowed grant type, scope
- Token handling policy: access token lifetime, refresh token rotation, revoke/logout behavior
- Security checklist cho redirect URI, PKCE, state parameter và token storage
- Test case cho invalid code, wrong redirect URI, expired token, wrong scope và refresh failure

## Decision Checklist / Câu hỏi kiểm tra

- Đây là authorization OAuth2 hay login identity bằng OIDC?
- Client là browser SPA, mobile app, backend server hay machine-to-machine service?
- Flow có dùng PKCE nếu client không giữ được secret an toàn không?
- Redirect URI có được allowlist chính xác không?
- Scope có theo least privilege không?
- Access token và refresh token được lưu ở đâu, có bị log/leak không?
- Resource server verify token, issuer, audience, expiry và scope thế nào?

## Failure Modes / Cách nó gây lỗi

- Dùng OAuth2 thay cho authentication làm app hiểu sai user identity hoặc tin access token không đủ claim.
- Redirect URI quá rộng tạo rủi ro code/token bị chuyển tới attacker.
- Không dùng PKCE cho public client làm authorization code dễ bị đánh cắp và đổi token.
- Scope quá rộng cấp quyền ngoài nhu cầu thật của client.
- Refresh token không rotate/revoke làm token bị leak vẫn dùng lâu dài.
- Resource server chỉ kiểm tra token tồn tại mà không kiểm tra issuer/audience/scope.

## Khi nào chưa cần hoặc dễ over-engineer

- App nội bộ đơn giản có thể dùng session/auth trực tiếp nếu không cần delegated third-party access.
- Không nên tự build authorization server nếu provider/framework uy tín đã đáp ứng nhu cầu.
- Không nên thêm nhiều grant type chỉ vì “đầy đủ OAuth”; mỗi flow thêm surface area và config risk.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Access Token]] vì OAuth2 cấp access token để client gọi resource server.
- [[Authorization]] vì OAuth2 là framework ủy quyền truy cập tài nguyên.
- [[OpenID Connect]] vì OIDC thêm identity layer trên OAuth2 cho login.
- [[JWT]] vì access token trong nhiều hệ thống được biểu diễn dưới dạng JWT.

## Liên quan rộng

- Identity provider
- Third-party API integration
- Login flow
- Token lifecycle
- API security

## Keywords / Từ khóa tìm kiếm

- OAuth2
- OAuth 2.0
- ủy quyền OAuth
- authorization code flow
- PKCE
- client credentials
- refresh token
- access token
- OAuth scope
- redirect URI
- state parameter
- delegated authorization
- resource server
- authorization server
- OAuth security

## Source trace

- RFC 6749
- OAuth 2.0 Security Best Current Practice
- OWASP OAuth 2.0 Security Cheat Sheet
