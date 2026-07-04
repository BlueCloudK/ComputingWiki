# CORS

Aliases: Cross-Origin Resource Sharing, chia sẻ tài nguyên khác origin

Type: Web Security / API

## Context / Ngữ cảnh

CORS xuất hiện khi JavaScript trong browser ở một origin cần gọi API/resource ở origin khác. Nó thường gặp khi frontend chạy ở domain/port khác backend, khi dùng CDN, API gateway, cookie/session cross-site hoặc khi local dev gọi API production/staging.

## Boundary / Ranh giới

### Nó là gì

CORS là cơ chế browser kiểm soát cross-origin request bằng các HTTP headers như `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, `Access-Control-Allow-Headers` và `Access-Control-Allow-Credentials`. Server khai báo origin nào được browser cho phép đọc response.

### Nó không phải là gì

CORS không phải authentication hoặc authorization. CORS chỉ là browser policy; nó không chặn server nhận request từ curl/Postman/server-to-server client. Nếu API thiếu auth, cấu hình CORS đúng cũng không bảo vệ dữ liệu. Ngược lại, lỗi CORS có thể xảy ra dù backend auth/API logic hoàn toàn đúng.

## Core Mechanism / Cơ chế lõi

Browser kiểm tra origin của frontend so với API. Với request đơn giản, browser gửi request rồi chỉ cho JavaScript đọc response nếu header CORS hợp lệ. Với request có method/header/content-type không đơn giản hoặc dùng credential, browser gửi preflight `OPTIONS` trước. Server phải trả đúng allow origin/method/header/credential thì request thật mới được browser tiếp tục.

## Project Role / Vai trò trong dự án

CORS là node cần mở khi frontend báo “blocked by CORS policy”, cookie không gửi qua domain khác, preflight fail, local dev gọi API không được, hoặc API gateway/proxy nuốt mất OPTIONS/header. Nó giúp team phân biệt lỗi browser policy, auth/session, proxy header hay backend endpoint.

## Output / Artifact nên có

- CORS policy theo environment: allowed origins, methods, headers, credentials
- Preflight handling rule cho `OPTIONS`
- Cookie/session cross-site note: SameSite, Secure, credentials mode
- Test case bằng browser/devtools cho simple request, preflight request và credential request
- Security review: không wildcard origin khi dùng credentials, không allow origin quá rộng cho API nhạy cảm

## Decision Checklist / Câu hỏi kiểm tra

- Frontend origin thật là gì: scheme, host, port?
- API có trả `Access-Control-Allow-Origin` đúng origin không?
- Request có credential/cookie không, và server có `Allow-Credentials` đúng không?
- Có dùng wildcard `*` cùng credentials không?
- Preflight `OPTIONS` có đi qua gateway/middleware/auth đúng cách không?
- Header client gửi có nằm trong `Access-Control-Allow-Headers` không?
- CORS config dev/staging/prod có khác nhau theo cách kiểm soát được không?

## Failure Modes / Cách nó gây lỗi

- API chạy đúng nhưng browser chặn vì thiếu/ sai CORS header.
- Preflight OPTIONS bị auth middleware chặn trước khi tới handler CORS.
- Allow origin wildcard quá rộng làm tăng rủi ro khi API dùng browser credential.
- Cookie không gửi vì frontend không set `credentials: include` hoặc SameSite/Secure sai.
- Proxy/CDN cache response CORS không có `Vary: Origin` làm origin này nhận header của origin khác.
- Local dev dùng port khác nên bị xem là cross-origin dù cùng localhost.

## Khi nào chưa cần hoặc dễ over-engineer

- Server-rendered app cùng origin với API có thể không cần cấu hình CORS riêng.
- Server-to-server integration không bị CORS vì CORS là browser enforcement.
- Không nên “fix CORS” bằng cách allow mọi origin nếu vấn đề thật là auth/session/proxy config.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Same Origin Policy]] vì CORS là cơ chế nới quyền có kiểm soát quanh same-origin policy.
- [[Middleware]] vì CORS thường được triển khai ở middleware/gateway layer.
- [[SPA]] vì SPA thường gọi API cross-origin và gặp CORS trong browser.
- [[Cookie]] vì credentialed CORS phụ thuộc SameSite/Secure/credentials mode.
- [[API Gateway]] vì gateway/proxy có thể xử lý hoặc phá CORS headers.

## Liên quan rộng

- Browser security
- Frontend backend integration
- API security
- Local development

## Keywords / Từ khóa tìm kiếm

- CORS
- Cross-Origin Resource Sharing
- chia sẻ tài nguyên khác origin
- Access-Control-Allow-Origin
- preflight request
- OPTIONS request
- Access-Control-Allow-Credentials
- allowed origin
- credentials include
- CORS error
- Same-Origin Policy
- Vary Origin
- CORS middleware
- browser blocked by CORS
- cors debugging

## Source trace

- MDN CORS documentation
- Fetch standard
