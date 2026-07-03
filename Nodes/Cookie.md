# Cookie

Aliases: HTTP cookie, browser cookie, cookie phiên

Type: Backend / Web Security

## Context / Ngữ cảnh

Cookie xuất hiện khi browser cần lưu một mẩu state nhỏ và tự gửi lại state đó theo request tới domain/path phù hợp. Trong web app, cookie thường liên quan tới session, login, CSRF protection, tracking preference, locale hoặc feature flag phía client/server.

## Boundary / Ranh giới

### Nó là gì

Cookie là cơ chế browser lưu key-value do server hoặc JavaScript đặt ra, rồi gửi kèm trong HTTP request nếu domain, path, expiry và SameSite/Secure rule cho phép. Với auth, cookie thường giữ session id hoặc refresh token, còn dữ liệu thật vẫn nên nằm ở server hoặc token đã kiểm soát.

### Nó không phải là gì

Cookie không phải database phía client và không nên chứa dữ liệu nhạy cảm dạng plain text. Cookie cũng không tự động an toàn: nếu thiếu HttpOnly, Secure, SameSite hoặc scope đúng, nó có thể bị lộ qua XSS, bị gửi trong cross-site request hoặc bị dùng sai domain/path.

## Core Mechanism / Cơ chế lõi

Server gửi `Set-Cookie` để browser lưu cookie với các thuộc tính như `HttpOnly`, `Secure`, `SameSite`, `Expires/Max-Age`, `Domain` và `Path`. Ở các request sau, browser tự gắn header `Cookie` nếu request khớp rule. Vì browser tự gửi cookie, cookie rất tiện cho session nhưng cũng phải thiết kế kỹ để tránh CSRF, scope rộng quá hoặc debug nhầm giữa client/server.

## Project Role / Vai trò trong dự án

Cookie ảnh hưởng trực tiếp tới login flow, session persistence, CSRF defense, browser debugging và behavior khác nhau giữa local/staging/production. Khi thiết kế web auth, team phải quyết định cookie chứa gì, domain/path nào được gửi, có cần HttpOnly/Secure/SameSite không, và frontend có cần đọc cookie đó hay không.

## Output / Artifact nên có

- Cookie policy cho auth/session: tên cookie, domain, path, expiry, SameSite, Secure, HttpOnly
- Session/cookie storage decision: cookie chứa session id, token hay preference
- Test case cho login/logout, expired cookie, cross-site request, subdomain và HTTPS-only behavior
- Debug checklist cho browser DevTools: Set-Cookie response, Cookie request header, domain/path mismatch
- Security review note cho CSRF, XSS exposure và token/session handling

## Decision Checklist / Câu hỏi kiểm tra

- Cookie auth/session có `HttpOnly` không nếu frontend không cần đọc?
- Production cookie có `Secure` và chỉ chạy qua HTTPS không?
- `SameSite` đang là Strict, Lax hay None, và có phù hợp flow OAuth/payment/cross-site không?
- Domain/path có quá rộng làm cookie gửi tới subdomain hoặc endpoint không cần thiết không?
- Cookie expiry có khớp session lifetime, refresh token lifetime và logout behavior không?
- Local/staging/production có khác domain/HTTPS làm cookie không được set hoặc không được gửi không?
- Có test CSRF hoặc cross-site request cho endpoint nhạy cảm không?

## Failure Modes / Cách nó gây lỗi

- Thiếu `HttpOnly` làm JavaScript đọc được cookie auth nếu có XSS.
- Thiếu `Secure` làm cookie có thể bị gửi qua HTTP trong môi trường sai cấu hình.
- `SameSite=None` sai hoặc thiếu `Secure` làm cookie không hoạt động trên browser hiện đại.
- Domain/path quá rộng làm cookie bị gửi tới nơi không cần, tăng rủi ro leak hoặc conflict.
- Cookie expiry lệch với server session khiến user bị logout bất ngờ hoặc vẫn đăng nhập sau khi tưởng đã hết phiên.
- Dev debug nhầm vì server đã `Set-Cookie` nhưng browser chặn do HTTPS, third-party cookie rule hoặc domain mismatch.

## Khi nào chưa cần hoặc dễ over-engineer

- App nội bộ rất nhỏ không có cross-site flow có thể dùng session cookie đơn giản với default bảo mật hợp lý.
- Không nên tự dựng cookie/session framework phức tạp nếu framework đã có session middleware an toàn.
- Không nên dùng cookie cho mọi state phía client; preference không nhạy cảm có thể dùng web storage tùy ngữ cảnh.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Session Management]] vì cookie thường giữ session id hoặc token để duy trì trạng thái đăng nhập.
- [[CSRF]] vì browser tự gửi cookie nên cross-site request có thể lợi dụng session nếu thiếu phòng vệ.
- [[XSS]] vì cookie không có HttpOnly có thể bị script đánh cắp.
- [[Same Origin Policy]] vì browser security model quyết định cookie và request cross-origin hoạt động ra sao.

## Liên quan rộng

- Browser security
- OAuth callback flow
- Frontend debugging
- Privacy and tracking

## Keywords / Từ khóa tìm kiếm

- Cookie
- HTTP cookie
- browser cookie
- session cookie
- Set-Cookie
- HttpOnly cookie
- Secure cookie
- SameSite cookie
- cookie domain
- cookie path
- cookie expiry
- third-party cookie
- cookie không gửi
- cookie phiên
- bảo mật cookie

## Source trace

- MDN Cookies
- RFC 6265
