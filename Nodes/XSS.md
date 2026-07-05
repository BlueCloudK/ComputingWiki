# XSS

Aliases: cross-site scripting, lỗi XSS

Type: Security

## Context / Ngữ cảnh

XSS xuất hiện khi dữ liệu không tin cậy được đưa vào HTML/DOM/JavaScript/CSS/URL context và browser thực thi hoặc diễn giải nó như code. Nó thường gặp ở comment, rich text, markdown preview, search result, profile field, admin dashboard, log viewer, template rendering và frontend DOM manipulation.

## Boundary / Ranh giới

### Nó là gì

XSS là lỗi cho phép attacker chèn script/markup độc hại vào trang mà người dùng khác hoặc chính attacker mở trong browser. Impact có thể là đánh cắp session token nếu token lộ được, thực hiện action thay user, thay đổi UI, exfiltrate data, keylogging hoặc pivot sang attack khác.

### Nó không phải là gì

XSS không chỉ được chặn bằng input validation. Defense chính là output encoding đúng context, sanitizer an toàn cho HTML cho phép, CSP defense-in-depth và tránh API nguy hiểm như `innerHTML` với dữ liệu không tin cậy. XSS cũng không phải CSRF, dù XSS có thể bypass nhiều CSRF defense.

## Core Mechanism / Cơ chế lõi

App nhận input, lưu hoặc render lại vào browser. Nếu dữ liệu được đặt vào HTML/attribute/JavaScript/CSS/URL context mà không encode/sanitize đúng, browser parse thành executable code. Stored XSS nằm trong dữ liệu lưu; reflected XSS phản chiếu từ request; DOM XSS xảy ra trong JavaScript client-side khi source không tin cậy đi vào sink nguy hiểm.

## Project Role / Vai trò trong dự án

XSS là node cần mở khi thiết kế frontend render user content, markdown/rich text, admin log viewer, template server-side hoặc SPA dùng DOM API. Nó giúp team phân biệt context encoding, HTML sanitization, CSP, cookie flags và data flow source→sink.

## Output / Artifact nên có

- XSS review checklist theo output context: HTML, attribute, JS, CSS, URL
- Sanitizer policy nếu cho phép rich text/HTML
- CSP policy và report-only rollout nếu dùng
- Test case cho stored/reflected/DOM XSS ở field quan trọng
- Cookie/session note: HttpOnly, Secure, SameSite để giảm impact khi XSS xảy ra

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu này có đến từ user/third-party/log/database không?
- Nó được render vào context nào: HTML text, attribute, JS string, CSS hay URL?
- Framework có auto-escape không, và có chỗ nào bypass như `dangerouslySetInnerHTML`/`innerHTML` không?
- Nếu cho phép rich text, sanitizer có allowlist tag/attribute/protocol không?
- CSP có chặn inline script và giới hạn script source không?
- Cookie/session token có HttpOnly để script không đọc trực tiếp không?
- Có test DOM source→sink cho frontend code không?

## Failure Modes / Cách nó gây lỗi

- Escape HTML text nhưng lại chèn vào JavaScript string context nên vẫn XSS.
- Markdown/rich text sanitizer cho phép `javascript:` URL hoặc event handler.
- Admin log viewer render raw request payload và tự XSS admin.
- SPA dùng `innerHTML` với dữ liệu API không tin cậy.
- CSP quá lỏng với `unsafe-inline` nên không giảm impact.
- Token lưu localStorage bị script độc hại đọc và exfiltrate.

## Khi nào chưa cần hoặc dễ over-engineer

- Page chỉ render static content không nhận dữ liệu không tin cậy có risk XSS thấp.
- Không nên tự viết sanitizer HTML nếu thư viện/framework uy tín đã có.
- Không nên xem CSP là fix chính nếu output encoding/sanitization vẫn sai.

## Gồm những gì

- [[Input Validation]]

## Nối mạnh

- [[CSP]] vì CSP là defense-in-depth quan trọng cho XSS.
- [[Cookie]] vì HttpOnly/SameSite/Secure giảm impact khi XSS xảy ra.
- [[Browser Security]] vì XSS khai thác browser execution context.
- [[Input Validation]] vì input validation giúp giảm payload lạ nhưng không thay output encoding.
- [[Session Management]] vì XSS có thể ảnh hưởng session/token handling.

## Liên quan rộng

- Output encoding
- DOM security
- Rich text sanitization
- Frontend security

## Keywords / Từ khóa tìm kiếm

- XSS
- cross-site scripting
- lỗi XSS
- stored XSS
- reflected XSS
- DOM XSS
- output encoding
- HTML sanitization
- dangerous innerHTML
- javascript URL
- CSP XSS
- cookie HttpOnly
- XSS prevention
- XSS debugging

## Source trace

- OWASP XSS Prevention Cheat Sheet
- OWASP DOM based XSS Prevention Cheat Sheet
