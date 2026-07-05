# Same Origin Policy

Aliases: SOP, same-origin policy, chính sách cùng origin

Type: Web Security / Browser

## Context / Ngữ cảnh

Same Origin Policy xuất hiện khi browser cần giới hạn script từ một origin đọc hoặc thao tác dữ liệu của origin khác. Đây là security boundary nền cho web app, ảnh hưởng tới CORS, cookie, iframe, localStorage/sessionStorage, frontend-backend domain và third-party integration.

## Boundary / Ranh giới

### Nó là gì

Same Origin Policy là browser security policy dựa trên origin: scheme, host và port. Hai URL chỉ cùng origin khi cả ba phần này giống nhau. SOP chủ yếu ngăn script từ origin A đọc DOM/storage/response nhạy cảm của origin B, trừ khi có cơ chế nới quyền như CORS hoặc postMessage đúng cách.

### Nó không phải là gì

Same Origin Policy không phải authentication hoặc authorization. Browser có thể chặn frontend đọc response cross-origin, nhưng backend vẫn phải kiểm tra quyền vì request có thể được gửi bằng tool khác hoặc qua form/navigation. SOP cũng không đồng nghĩa với same-site; subdomain khác thường là khác origin dù có thể same-site cho cookie.

## Core Mechanism / Cơ chế lõi

Browser gắn origin cho document/script và so sánh origin đó với resource đích. Cross-origin write như form submit/navigation thường được phép ở mức nhất định, nhưng cross-origin read bị chặn nếu không có CORS. Cookie lại theo domain/SameSite rule riêng, nên request có thể gửi cookie dù script không đọc được response.

## Project Role / Vai trò trong dự án

Same Origin Policy là node cần mở khi debug CORS error, cookie không gửi, SPA gọi API khác domain, iframe embed, OAuth callback, CDN/static asset hoặc local dev frontend/backend khác port. Nó giúp team phân biệt browser block, backend auth failure và cookie/SameSite issue.

## Output / Artifact nên có

- Origin matrix: frontend, API, auth domain, CDN, admin, third-party
- CORS decision: origin allowlist, credential mode, allowed headers/methods
- Cookie/domain/SameSite/Secure decision nếu auth dựa vào cookie
- postMessage/iframe rule nếu cross-origin embed cần giao tiếp
- Browser test cho login, API call, upload, embedded page và redirect flow

## Decision Checklist / Câu hỏi kiểm tra

- Frontend và API có cùng scheme, host, port không?
- Flow cần gửi request cross-origin hay cần đọc response cross-origin?
- Credential/cookie có cần gửi cross-origin không?
- CORS rule có allow đúng origin cụ thể hay mở wildcard quá rộng không?
- Cookie SameSite/domain/path/Secure có khớp flow không?
- Subdomain này là same-origin, same-site hay hoàn toàn cross-site?
- Nếu dùng iframe/postMessage, target origin có được kiểm tra chặt không?

## Failure Modes / Cách nó gây lỗi

- Debug nhầm backend vì browser chặn response trước khi app đọc được.
- Mở CORS wildcard hoặc reflect origin bừa làm lộ response credentialed.
- Nhầm subdomain là cùng origin trong khi browser coi là khác origin.
- Cookie không gửi do SameSite/Secure/domain sai, nhưng team tưởng auth code lỗi.
- postMessage không check target/source origin làm lộ data cho iframe/window sai.
- Local dev khác port bị CORS trong khi production same-origin hoặc ngược lại.

## Khi nào chưa cần hoặc dễ over-engineer

- App chỉ chạy một origin đơn giản có thể chưa cần proxy/CORS phức tạp.
- Không nên thêm CORS rộng để “fix nhanh” khi lỗi thật là cookie/SameSite hoặc API domain sai.
- Không nên dùng SOP như defense backend; server-side authorization vẫn bắt buộc.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CORS]] vì CORS là cơ chế nới quyền có kiểm soát trên nền Same Origin Policy.
- [[Cookie]] vì cookie domain, SameSite và Secure flag thường bị debug cùng origin boundary.
- [[CSRF]] vì browser có thể gửi credential cross-site dù script không đọc được response.
- [[Security Header]] vì một số browser policy được enforce qua HTTP security headers.
- [[SPA]] vì SPA gọi API/CDN/auth domain thường vướng origin boundary.

## Liên quan rộng

- Browser security
- Frontend integration
- API boundary
- Web authentication

## Keywords / Từ khóa tìm kiếm

- Same Origin Policy
- SOP
- same-origin policy
- chính sách cùng origin
- browser origin
- cross-origin
- same-site
- scheme host port
- CORS error
- credentialed request
- postMessage origin
- iframe origin
- local dev CORS
- same origin debugging

## Source trace

- MDN Web Docs / Same-origin policy
- WHATWG HTML / origin
