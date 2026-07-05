# CSRF

Aliases: cross-site request forgery, lỗi CSRF

Type: Security

## Context / Ngữ cảnh

CSRF xuất hiện khi browser tự động gửi credential như cookie/session tới một website và attacker có thể dụ user đã đăng nhập gửi request state-changing từ site khác. Nó thường liên quan tới form POST, cookie-based session, admin action, banking/order/change-email endpoint và endpoint không yêu cầu token xác nhận riêng.

## Boundary / Ranh giới

### Nó là gì

CSRF là lỗi cho phép attacker ép browser của victim gửi request hợp lệ về site mục tiêu với cookie/session của victim. Server thấy request có session hợp lệ và thực hiện action dù user không chủ động thao tác trên site thật.

### Nó không phải là gì

CSRF không phải XSS. XSS chạy script trong origin của site mục tiêu; CSRF lợi dụng browser tự gửi cookie cross-site. CSRF cũng không ảnh hưởng giống nhau tới bearer token trong Authorization header nếu attacker không đọc/gửi được header đó từ site khác, nhưng vẫn cần kiểm tra flow cụ thể.

## Core Mechanism / Cơ chế lõi

Attacker tạo form/image/fetch/navigation từ origin khác tới endpoint state-changing. Browser tự attach cookie theo SameSite/domain/path rule. Defense gồm CSRF token per session/request, SameSite cookie, kiểm tra Origin/Referer, yêu cầu custom header cho AJAX, re-auth/step-up cho action nhạy cảm và không dùng GET cho state change.

## Project Role / Vai trò trong dự án

CSRF là node cần mở khi app dùng cookie session, server-rendered forms, admin panel hoặc API nhận request credentialed từ browser. Nó giúp team review endpoint nào làm thay đổi state, cookie SameSite ra sao và token/header/origin check có được enforce ở backend không.

## Output / Artifact nên có

- CSRF risk inventory: endpoint state-changing dùng cookie/session
- CSRF token strategy: generation, binding, validation, expiry, rotation
- Cookie policy: SameSite, Secure, HttpOnly, domain/path
- Origin/Referer/custom header rule nếu dùng cho API
- Test case: cross-site form POST, missing token, invalid token, SameSite behavior

## Decision Checklist / Câu hỏi kiểm tra

- Endpoint này có thay đổi state không?
- Request có dựa vào cookie/session tự gửi bởi browser không?
- Cookie SameSite là Lax/Strict/None và có phù hợp flow không?
- State-changing request có CSRF token hoặc Origin/Referer/custom header check không?
- Có endpoint GET nào thay đổi state không?
- Action nhạy cảm có cần re-auth/confirm step không?
- XSS nếu xảy ra có thể bypass CSRF token không, và CSP/HttpOnly đã giảm impact chưa?

## Failure Modes / Cách nó gây lỗi

- Form đổi email/password/order action thiếu CSRF token.
- Cookie `SameSite=None` dùng cho cross-site flow nhưng thiếu defense khác.
- Endpoint GET làm state change và bị trigger bằng image/link.
- CSRF token không bind session hoặc token static nên attacker reuse được.
- Chỉ check CORS và tưởng chặn được CSRF, trong khi browser vẫn gửi form/navigation.
- Origin/Referer check bị bỏ qua cho một số endpoint hoặc proxy làm mất header.

## Khi nào chưa cần hoặc dễ over-engineer

- API chỉ dùng Authorization bearer token không tự attach bởi browser có CSRF risk thấp hơn, nhưng vẫn cần xem token được lưu/gửi thế nào.
- Endpoint read-only không thay đổi state thường không cần CSRF token.
- Không nên chỉ dựa vào SameSite nếu app có flow cross-site phức tạp hoặc browser compatibility cần cân nhắc.

## Gồm những gì

- [[Authentication]]

## Nối mạnh

- [[Cookie]] vì CSRF phụ thuộc browser tự gửi cookie theo SameSite/domain/path.
- [[Session Management]] vì session cookie là credential thường bị lợi dụng trong CSRF.
- [[Browser Security]] vì CSRF là hành vi browser credential/request boundary.
- [[CORS]] vì CORS không phải defense chính cho form-based CSRF và dễ bị hiểu nhầm.
- [[XSS]] vì XSS có thể bypass hoặc đánh cắp CSRF token nếu app không phòng thủ tốt.

## Liên quan rộng

- Web security
- SameSite cookie
- Server-rendered forms
- State-changing endpoint

## Keywords / Từ khóa tìm kiếm

- CSRF
- cross-site request forgery
- lỗi CSRF
- CSRF token
- anti-CSRF token
- SameSite cookie
- Origin header check
- Referer header check
- state changing request
- cookie session CSRF
- form POST CSRF
- CSRF prevention
- CSRF debugging

## Source trace

- OWASP CSRF Prevention Cheat Sheet
