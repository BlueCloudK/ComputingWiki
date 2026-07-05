# HTTPS

Aliases: HTTP over TLS, secure HTTP, HTTP bảo mật

Type: Protocol / Data Format

## Context / Ngữ cảnh

HTTPS xuất hiện khi web/API traffic cần dùng HTTP semantics trên kênh truyền được bảo vệ bằng TLS. Nó là baseline cho website, API, login/session, webhook callback, admin panel và hầu hết traffic qua internet.

## Boundary / Ranh giới

### Nó là gì

HTTPS là HTTP chạy qua TLS. Client tạo TLS connection tới server, validate certificate/hostname, rồi gửi HTTP request/response bên trong encrypted channel. HTTPS giúp chống nghe lén và sửa đổi dữ liệu trên đường truyền, đồng thời xác thực server qua certificate.

### Nó không phải là gì

HTTPS không phải security toàn diện cho API hoặc web app. Nó không thay thế authentication, authorization, input validation, CSRF/XSS defense hoặc secret management. HTTPS cũng không bảo vệ secret nếu secret bị đặt trong URL query rồi bị log ở server/proxy/browser history.

## Core Mechanism / Cơ chế lõi

Browser/client kết nối tới `https://`, thực hiện TLS handshake, kiểm tra certificate chain và hostname, rồi truyền HTTP qua encrypted channel. Web deployment thường enforce redirect từ HTTP sang HTTPS, bật HSTS nếu phù hợp, và cấu hình reverse proxy/load balancer để app biết original scheme.

## Project Role / Vai trò trong dự án

HTTPS là node cần mở khi debug browser padlock, mixed content, redirect loop, cookie Secure không gửi, webhook/provider yêu cầu HTTPS hoặc certificate hết hạn. Nó giúp team phân biệt lỗi HTTP layer, TLS/certificate layer và reverse proxy scheme forwarding.

## Output / Artifact nên có

- HTTPS endpoint và redirect policy: HTTP → HTTPS
- Certificate owner, provider và renewal/expiry monitoring
- HSTS policy nếu domain public đã sẵn sàng enforce HTTPS lâu dài
- Proxy/LB header config: `X-Forwarded-Proto`, `Host`, redirect behavior
- Test checklist: cert chain, mixed content, Secure cookie, redirect loop

## Decision Checklist / Câu hỏi kiểm tra

- Endpoint public có enforce HTTPS không?
- Certificate có đúng domain/subdomain và chain không?
- HTTP có redirect sang HTTPS đúng cách không, có redirect loop không?
- Cookie nhạy cảm có `Secure` và chỉ gửi qua HTTPS không?
- App sau proxy có biết original scheme là HTTPS không?
- Có mixed content khiến browser block JS/CSS/image/API không?
- Secret/token có bị đặt trong URL query và log lại không?

## Failure Modes / Cách nó gây lỗi

- HTTP endpoint còn mở làm token/session có thể bị lộ trên mạng.
- Certificate hết hạn/sai chain làm browser/API client từ chối kết nối.
- Mixed content làm browser block resource trên trang HTTPS.
- Reverse proxy không set scheme header làm app redirect HTTP/HTTPS vòng lặp.
- Secure cookie không gửi ở local/staging vì endpoint đang dùng HTTP.
- Token trong URL query bị log ở browser history, proxy log hoặc analytics.

## Khi nào chưa cần hoặc dễ over-engineer

- Local-only prototype có thể dùng HTTP, nhưng không nên đem assumption đó lên staging/production.
- Không nên tự quản TLS/certificate nếu managed TLS ở CDN/LB đủ dùng và ít risk hơn.
- Không nên bật HSTS dài hạn khi chưa chắc toàn bộ subdomain đã hỗ trợ HTTPS đúng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTP]] vì HTTPS giữ HTTP request/response semantics.
- [[TLS]] vì TLS cung cấp encrypted authenticated channel cho HTTPS.
- [[Transport Layer Protection]] vì HTTPS là control phổ biến nhất cho web/API data in transit.
- [[Cookie]] vì cookie `Secure` và SameSite behavior gắn chặt với HTTPS.
- [[Reverse Proxy]] vì HTTPS thường terminate ở proxy/LB/CDN.

## Liên quan rộng

- Web security
- Certificate management
- Browser behavior
- API deployment

## Keywords / Từ khóa tìm kiếm

- HTTPS
- HTTP over TLS
- secure HTTP
- HTTP bảo mật
- TLS certificate
- browser padlock
- encrypted web traffic
- HTTPS redirect
- HSTS
- mixed content
- Secure cookie
- redirect loop
- certificate expired
- HTTPS debugging

## Source trace

- Computer Networks Map
- OWASP Transport Layer Protection Cheat Sheet
