# CSP

Aliases: Content Security Policy, chính sách bảo mật nội dung

Type: Security / Web

## Context / Ngữ cảnh

CSP xuất hiện khi web app cần giới hạn nguồn script, style, image, font, frame, connect endpoint hoặc worker mà browser được phép tải/chạy. Nó thường dùng để giảm impact của XSS, phát hiện injection và kiểm soát tài nguyên third-party trên trang.

## Boundary / Ranh giới

### Nó là gì

CSP là browser security policy được gửi qua HTTP header `Content-Security-Policy` hoặc meta tag để định nghĩa nguồn nội dung hợp lệ. Các directive như `script-src`, `style-src`, `img-src`, `connect-src`, `frame-ancestors`, nonce/hash và report-uri/report-to quyết định browser cho phép hay chặn tài nguyên nào.

### Nó không phải là gì

CSP không thay thế việc fix XSS ở code. Nó là defense-in-depth: nếu input/output encoding, sanitization hoặc dependency bị lỗi, CSP có thể giảm khả năng script độc hại chạy. CSP yếu kiểu cho phép `unsafe-inline` rộng hoặc wildcard quá nhiều thì gần như không còn giá trị bảo vệ.

## Core Mechanism / Cơ chế lõi

Browser đọc policy, so sánh mỗi resource/script/action với directive tương ứng, rồi cho phép hoặc chặn. Với script inline, CSP mạnh thường dùng nonce hoặc hash để chỉ script được server đánh dấu mới chạy. Report-only mode cho phép thử policy và thu violation report trước khi enforce chính thức.

## Project Role / Vai trò trong dự án

CSP ảnh hưởng tới frontend build, third-party script, CDN, analytics, auth redirect, iframe embedding và security review. Khi triển khai web app, team cần biết script/style nào hợp lệ, inline script có cần nonce/hash không, môi trường dev/prod khác gì và violation report được theo dõi ở đâu.

## Output / Artifact nên có

- CSP header policy theo environment
- Danh sách source hợp lệ cho script/style/img/connect/frame
- Nonce/hash strategy nếu app dùng inline script
- Report-only rollout plan và violation report endpoint/dashboard
- Test case cho XSS payload cơ bản, blocked script, third-party script và auth/iframe flow

## Decision Checklist / Câu hỏi kiểm tra

- Policy có chặn inline script không, hay đang dùng `unsafe-inline`?
- Có cần nonce/hash cho script hợp lệ không?
- `script-src`, `connect-src`, `frame-ancestors` có quá rộng không?
- Third-party analytics/CDN/payment/auth provider có được allowlist đúng không?
- Có dùng report-only trước khi enforce để tránh làm gãy production không?
- Violation report có được thu và review không?
- CSP có khác nhau giữa dev/staging/prod theo cách kiểm soát được không?

## Failure Modes / Cách nó gây lỗi

- Policy quá lỏng cho phép wildcard hoặc unsafe-inline làm CSP không chặn XSS hiệu quả.
- Policy quá chặt làm app không tải được script/style/CDN hợp lệ ở production.
- Thiếu `connect-src` cho API/websocket làm frontend gọi backend fail.
- Thiếu `frame-ancestors` hoặc cấu hình sai làm embedding/clickjacking protection không đúng.
- Không dùng report-only trước khi enforce làm deploy CSP gây lỗi người dùng thật.
- CSP chỉ đặt trong meta tag nên một số directive/header behavior không hoạt động như mong muốn.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype nội bộ chưa expose rộng có thể bắt đầu bằng policy đơn giản và XSS hygiene trước.
- Không nên viết policy cực phức tạp khi frontend còn thay đổi mạnh và chưa có report workflow.
- Không nên coi CSP là lý do bỏ qua escaping/sanitization/input validation.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[XSS]] vì CSP là defense-in-depth quan trọng để giảm impact của XSS.
- [[Browser Security]] vì CSP được enforce bởi browser.
- [[Same Origin Policy]] vì cả hai đều thuộc browser security model nhưng giải quyết boundary khác nhau.
- [[Frontend Security]] vì CSP cần phối hợp với frontend build và third-party resources.

## Liên quan rộng

- Application security
- Threat modeling
- Web hardening
- Third-party script governance

## Keywords / Từ khóa tìm kiếm

- CSP
- Content Security Policy
- chính sách bảo mật nội dung
- script-src
- style-src
- connect-src
- frame-ancestors
- nonce
- hash
- unsafe-inline
- report-only
- violation report
- CSP header
- XSS mitigation
- browser security policy

## Source trace

- MDN Content Security Policy
- OWASP Content Security Policy Cheat Sheet
