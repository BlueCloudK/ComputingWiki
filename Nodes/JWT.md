# JWT

Aliases: JSON Web Token, token JWT, bearer token

Type: Backend Security

## Context / Ngữ cảnh

JWT xuất hiện trong authentication/authorization flow khi client hoặc service cần gửi một token chứa claims đã được ký. Nó thường đi trong header `Authorization: Bearer <token>`, dùng giữa frontend-backend, mobile-backend hoặc service-to-service.

## Boundary / Ranh giới

### Nó là gì

JWT là một token có cấu trúc gồm header, payload và signature. Payload chứa claims như subject, issuer, audience, role/scope, issued time và expiration. Signature giúp bên nhận kiểm tra token có bị sửa hay không.

### Nó không phải là gì

JWT không tự động đồng nghĩa với session an toàn. Nó không mã hóa payload mặc định, nên không nên nhét secret hoặc dữ liệu nhạy cảm vào token. JWT cũng không tự giải quyết logout, revoke token, refresh token hay phân quyền đúng.

## Core Mechanism / Cơ chế lõi

Bên phát hành token ký header + payload bằng secret hoặc private key. Bên nhận verify signature, kiểm tra `exp`, `iss`, `aud`, algorithm và claims trước khi tin token. Nếu dùng access token ngắn hạn + refresh token, hệ thống cần cơ chế cấp lại, rotate và thu hồi token hợp lý.

## Project Role / Vai trò trong dự án

JWT ảnh hưởng trực tiếp tới login, session, authorization, API security và service-to-service authentication. Khi thiết kế auth, team phải quyết định token nằm ở đâu, sống bao lâu, chứa claim gì, verify ở layer nào, refresh/revoke ra sao và log/debug lỗi token thế nào.

## Output / Artifact nên có

- Token claim schema: subject, issuer, audience, expiration, issued time, role/scope nếu có
- JWT verification rule: algorithm, signing key/JWKS, issuer, audience, expiry
- Access token / refresh token strategy
- Storage decision: cookie, memory, mobile secure storage hoặc service secret
- Test case cho expired token, invalid signature, wrong audience, missing scope và revoked token

## Decision Checklist / Câu hỏi kiểm tra

- JWT có được verify signature ở mọi protected endpoint không?
- Có kiểm tra expiration, issuer, audience và algorithm không?
- Payload có chứa dữ liệu nhạy cảm không?
- Token lưu ở đâu: cookie, localStorage, memory hay secure storage?
- Logout/revoke token xử lý thế nào?
- Access token sống bao lâu, refresh token sống bao lâu?
- Role/scope trong token có bị stale khi quyền user thay đổi không?

## Failure Modes / Cách nó gây lỗi

- Không verify signature hoặc verify sai algorithm làm attacker giả token.
- Nhét dữ liệu nhạy cảm vào payload vì tưởng JWT được mã hóa.
- Token sống quá lâu nên user bị mất quyền nhưng vẫn truy cập được.
- Không kiểm tra audience/issuer làm token của hệ khác dùng nhầm được.
- Lưu JWT trong localStorage làm tăng rủi ro khi có XSS.
- Không có revoke/rotation strategy nên logout hoặc khóa tài khoản không có hiệu lực ngay.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ server-rendered có thể dùng server-side session đơn giản hơn JWT.
- Không nên dùng JWT chỉ vì “stateless” nếu vẫn cần revoke/logout realtime phức tạp.
- Service nội bộ ít endpoint có thể dùng session, API key hoặc mTLS tùy ngữ cảnh thay vì tự dựng JWT flow phức tạp.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authentication]] vì JWT thường được phát hành sau login để chứng minh user/service là ai.
- [[Authorization]] vì role/scope trong JWT thường được dùng để quyết định quyền truy cập.
- [[Session Management]] vì JWT thay đổi cách hệ thống duy trì trạng thái đăng nhập.
- [[API Security]] vì lỗi verify, storage hoặc revoke JWT là lỗi bảo mật API phổ biến.

## Liên quan rộng

- OAuth
- OpenID Connect
- Cookie security
- XSS
- Service-to-service authentication

## Keywords / Từ khóa tìm kiếm

- JWT
- JSON Web Token
- bearer token
- access token
- refresh token
- token claims
- token signature
- JWT verification
- JWT expiration
- JWT revoke
- algorithm confusion
- bearer authentication
- token đăng nhập
- xác thực bằng token

## Source trace

- RFC 7519
- OWASP JSON Web Token for Java Cheat Sheet
