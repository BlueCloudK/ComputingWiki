# JWT Attack

Aliases: JWT Attack, JWT vulnerability, JSON Web Token attack, tấn công JWT

Type: Security

## Context / Ngữ cảnh

JWT Attack xuất hiện khi hệ thống dùng JSON Web Token cho auth/API nhưng verify token, validate claim, quản lý key hoặc lưu trữ token sai. Nó thường liên quan tới login API, protected endpoint, service-to-service auth, mobile/backend hoặc SPA/backend.

## Boundary / Ranh giới

### Nó là gì

JWT Attack là nhóm lỗi khai thác JWT như bỏ verify signature, chấp nhận algorithm không an toàn, validate thiếu `iss/aud/exp`, dùng key yếu, để token sống quá lâu hoặc leak token qua storage/log. Điểm chung là attacker khiến server tin một token không nên được tin.

### Nó không phải là gì

JWT Attack không phải mọi lỗi authentication. Nếu lỗi nằm ở password, session fixation, CSRF hoặc broken access control thì cần gọi đúng node đó. JWT Attack cũng không đồng nghĩa với “JWT xấu”; vấn đề thường là verify, claim, key, lifetime, storage hoặc revoke strategy sai.

## Core Mechanism / Cơ chế lõi

JWT an toàn khi bên nhận verify signature bằng key đúng, chỉ cho phép algorithm mong đợi, kiểm tra issuer, audience, expiry và claim quyền trước khi cấp access. Attack xảy ra khi một trong các bước này bị bỏ qua hoặc cấu hình sai, làm token giả, token của hệ khác, token hết hạn hoặc token quyền cũ vẫn được chấp nhận.

## Project Role / Vai trò trong dự án

JWT Attack là node cần mở khi review auth middleware, API gateway, login service, token refresh flow hoặc service-to-service authentication. Nó giúp team biến câu “auth có vẻ ổn” thành checklist cụ thể: verify gì, key ở đâu, token sống bao lâu, quyền trong token có stale không, revoke/logout có hiệu lực không.

## Output / Artifact nên có

- JWT security checklist cho auth middleware/API gateway
- Test case cho invalid signature, expired token, wrong issuer, wrong audience, missing scope và revoked token
- Algorithm allowlist và key/JWKS rotation policy
- Token lifetime và refresh/revoke decision note
- Logging rule để không log access token/refresh token ra file hoặc monitoring

## Decision Checklist / Câu hỏi kiểm tra

- Backend có verify signature ở mọi protected endpoint không?
- Có khóa algorithm thành allowlist cụ thể không, hay tin giá trị `alg` từ token?
- Có kiểm tra `exp`, `nbf`, `iss`, `aud` và scope/role không?
- Key/JWKS có rotation, cache và fallback an toàn không?
- Token có bị log ra request log, error log hoặc analytics không?
- Nếu user bị khóa hoặc đổi quyền, token cũ còn dùng được bao lâu?
- Refresh token có rotation/reuse detection không nếu hệ thống cần bảo mật cao?

## Failure Modes / Cách nó gây lỗi

- Bỏ verify signature làm attacker tự tạo token với quyền admin.
- Chấp nhận algorithm sai hoặc key confusion làm token được ký bằng cách không mong muốn.
- Không kiểm tra audience/issuer làm token của app/service khác dùng nhầm được.
- Không kiểm tra expiry làm token hết hạn vẫn truy cập được.
- Token chứa role/scope quá lâu khiến user bị thu hồi quyền nhưng token cũ vẫn còn quyền.
- Log hoặc lưu token ở nơi không an toàn làm attacker chiếm phiên bằng bearer token.

## Khi nào chưa cần hoặc dễ over-engineer

- App server-rendered nhỏ dùng server-side session có thể không cần JWT attack checklist riêng.
- Không nên thêm hệ thống token blacklist phức tạp nếu access token rất ngắn hạn và risk chấp nhận được.
- Không nên dùng JWT chỉ vì “microservice standard” nếu revoke/logout realtime là yêu cầu chính và session server-side đơn giản hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JWT]] vì attack phụ thuộc trực tiếp vào cách JWT được phát hành, verify, lưu trữ và thu hồi.
- [[Authentication]] vì JWT attack thường phá vỡ việc chứng minh danh tính user/service.
- [[Authorization]] vì claim role/scope sai có thể dẫn tới leo quyền.
- [[API Security]] vì protected API thường là nơi JWT bị validate sai.

## Liên quan rộng

- OAuth
- OpenID Connect
- Key rotation
- Bearer token theft
- Security testing

## Keywords / Từ khóa tìm kiếm

- JWT Attack
- JWT vulnerability
- JSON Web Token attack
- tấn công JWT
- JWT verification bypass
- algorithm confusion
- alg none
- invalid signature
- token forgery
- expired token accepted
- wrong audience
- wrong issuer
- JWT key rotation
- bearer token theft

## Source trace

- OWASP JSON Web Token for Java Cheat Sheet
- RFC 7519
