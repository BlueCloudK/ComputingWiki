# OpenID Connect

Aliases: OpenID Connect, OIDC, đăng nhập OIDC

Type: Backend Engineering

## Context / Ngữ cảnh

OpenID Connect xuất hiện khi application cần đăng nhập user qua identity provider và nhận thông tin identity chuẩn hóa trên nền OAuth2. Nó thường dùng trong “Login with Google/Microsoft/GitHub”, enterprise SSO, mobile/web login, B2B SaaS và hệ thống cần federated identity.

## Boundary / Ranh giới

### Nó là gì

OpenID Connect là identity layer trên OAuth2. Nó thêm ID token, user info endpoint, discovery metadata và chuẩn claim để client xác minh user là ai. OIDC trả lời câu hỏi “user này là ai và được provider xác thực thế nào”.

### Nó không phải là gì

OpenID Connect không thay thế authorization rule của application. ID token chứng minh identity, không tự quyết định user được làm gì trong domain của app. OIDC cũng không giống OAuth2 thuần; access token dùng gọi resource server, còn ID token dùng cho client xác minh login/user identity.

## Core Mechanism / Cơ chế lõi

OIDC thường dùng authorization code flow với PKCE. Sau khi user login ở identity provider, client/backend nhận code, đổi lấy token, verify ID token signature, issuer, audience, expiry, nonce nếu có, rồi map subject/claims sang user/session nội bộ. Discovery document và JWKS giúp client biết endpoint và public key để verify token.

## Project Role / Vai trò trong dự án

OpenID Connect ảnh hưởng tới login architecture, SSO, user provisioning, session creation, account linking và security review. Khi thiết kế login, team phải quyết định provider nào tin, claim nào dùng làm identity, token verify ở đâu, user nội bộ được tạo/map thế nào và logout/session lifecycle ra sao.

## Output / Artifact nên có

- OIDC provider config: issuer, client id, redirect URI, scopes, discovery URL
- ID token verification rule: signature, issuer, audience, expiry, nonce/state
- User mapping/account linking decision: subject, email, tenant, organization claim
- Login/session flow diagram từ redirect tới session nội bộ
- Test case cho wrong issuer, wrong audience, expired ID token, replay/state mismatch và missing claim

## Decision Checklist / Câu hỏi kiểm tra

- App đang cần authentication bằng OIDC hay authorization bằng OAuth2?
- ID token có được verify signature, issuer, audience và expiry không?
- Claim nào được dùng làm user identity: `sub`, email hay tenant-specific claim?
- Email có được xem là verified không, và có thể thay đổi không?
- State/nonce có được dùng để chống CSRF/replay trong login flow không?
- Account linking có tránh chiếm tài khoản bằng email trùng không?
- Logout khỏi app có cần logout khỏi identity provider không?

## Failure Modes / Cách nó gây lỗi

- Tin ID token mà không verify issuer/audience làm token của app khác dùng nhầm được.
- Dùng email làm primary identity khi email có thể đổi hoặc chưa verified.
- Thiếu state/nonce làm login flow dễ bị CSRF/replay.
- Nhầm access token với ID token dẫn tới verify sai hoặc lấy identity từ token không phù hợp.
- Account linking sai làm user từ provider khác chiếm tài khoản hiện có.
- Không xử lý key rotation/JWKS cache làm login fail khi provider rotate key.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ không cần SSO/federated login có thể dùng local auth/session đơn giản hơn.
- Không nên tự implement OIDC protocol từ đầu nếu thư viện/provider đã hỗ trợ chuẩn.
- Không nên đưa toàn bộ authorization domain vào claim OIDC nếu quyền app thay đổi thường xuyên và cần kiểm soát nội bộ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[OAuth2]] vì OIDC được xây trên OAuth2 flow và token exchange.
- [[Authentication]] vì OIDC dùng để xác thực identity của user.
- [[JWT]] vì ID token thường là JWT cần verify đúng.
- [[Session Management]] vì sau OIDC login app thường tạo session nội bộ.

## Liên quan rộng

- Identity provider
- Single Sign-On
- Account linking
- Enterprise login
- User provisioning

## Keywords / Từ khóa tìm kiếm

- OpenID Connect
- OIDC
- đăng nhập OIDC
- ID token
- identity provider
- issuer
- audience
- JWKS
- discovery document
- nonce
- state parameter
- single sign on
- federated login
- account linking
- login callback

## Source trace

- OpenID Connect Core 1.0
- OpenID Connect Discovery 1.0
- OWASP Authentication Cheat Sheet
