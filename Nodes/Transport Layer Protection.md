# Transport Layer Protection

Aliases: transport security, bảo vệ dữ liệu truyền tải

Type: Security

## Context / Ngữ cảnh

Transport Layer Protection xuất hiện khi dữ liệu đi qua network cần chống nghe lén, sửa đổi hoặc giả mạo. Nó thường áp dụng cho web/API traffic, service-to-service call, webhook, database connection, admin interface và bất kỳ kênh nào truyền credential, PII hoặc dữ liệu nhạy cảm.

## Boundary / Ranh giới

### Nó là gì

Transport Layer Protection là nhóm control bảo vệ data in transit bằng TLS/HTTPS, certificate validation, protocol/cipher an toàn, HSTS hoặc mTLS nếu cần. Nó đảm bảo client nói chuyện với đúng peer và dữ liệu trên đường truyền được mã hóa/chống sửa đổi.

### Nó không phải là gì

Transport Layer Protection không bảo vệ dữ liệu sau khi đã tới client/server và không thay thế authentication/authorization. HTTPS/TLS không làm API logic an toàn nếu token bị lộ ở log, endpoint thiếu auth hoặc server bị compromise.

## Core Mechanism / Cơ chế lõi

Client và server thiết lập encrypted authenticated channel qua TLS handshake, validate certificate/hostname, thỏa thuận key/cipher rồi truyền data qua record layer đã mã hóa. Security phụ thuộc vào TLS version, certificate chain, private key protection, renewal, redirect policy và việc không tắt certificate verification.

## Project Role / Vai trò trong dự án

Transport Layer Protection là node cần mở khi thiết kế API/webhook, debug HTTPS/cert error, enforce HTTPS sau reverse proxy/load balancer, hoặc review vì sao token/session không được gửi qua HTTP. Nó giúp team biết kênh nào cần TLS, TLS terminate ở đâu và client có verify peer đúng không.

## Output / Artifact nên có

- TLS/HTTPS policy: endpoint nào bắt buộc HTTPS/TLS
- Certificate ownership/renewal/expiry monitoring plan
- Protocol/cipher baseline và deprecated version bị chặn
- Proxy/LB termination note: TLS terminate ở CDN/LB/proxy/app
- Test/check: cert chain, hostname validation, HTTP redirect, HSTS nếu là web

## Decision Checklist / Câu hỏi kiểm tra

- Traffic có chứa credential, session token, PII hoặc dữ liệu nhạy cảm không?
- Endpoint có enforce HTTPS/TLS không hay vẫn cho HTTP?
- Certificate có đúng hostname, chain và chưa hết hạn không?
- Client có verify certificate/hostname hay đang tắt verification?
- TLS terminate ở đâu và upstream/internal traffic còn được bảo vệ không?
- Protocol/cipher cũ có bị disable không?
- Có monitoring trước khi certificate hết hạn không?

## Failure Modes / Cách nó gây lỗi

- Dùng HTTP cho token/session làm credential bị nghe lén.
- Tắt certificate verification để “fix nhanh” và mở MITM risk.
- Certificate hết hạn làm client không kết nối được.
- Sai hostname/SNI/chain làm một số client fail nhưng browser/local có thể vẫn chạy.
- Reverse proxy terminate TLS nhưng app không biết original scheme, gây redirect loop.
- Mixed content làm browser block resource trên trang HTTPS.

## Khi nào chưa cần hoặc dễ over-engineer

- Local throwaway prototype không dữ liệu nhạy có thể chưa cần formal TLS policy.
- Không nên tự quản certificate/cipher phức tạp nếu managed TLS đã đủ cho threat model.
- Không nên bật mTLS nội bộ khi team chưa có certificate lifecycle/rotation đủ ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[TLS]] vì TLS là cơ chế chính để bảo vệ kênh truyền.
- [[HTTPS]] vì web/API thường dùng HTTP chạy qua TLS.
- [[Session Management]] vì session token cần truyền qua channel an toàn.
- [[Secret]] vì secret/API key không nên đi qua kênh không mã hóa.
- [[Reverse Proxy]] vì TLS thường terminate ở proxy/LB/CDN trước app.

## Liên quan rộng

- Data in transit
- Certificate management
- Web/API security
- Service-to-service security

## Keywords / Từ khóa tìm kiếm

- Transport Layer Protection
- transport security
- bảo vệ dữ liệu truyền tải
- TLS configuration
- HTTPS enforcement
- certificate validation
- certificate renewal
- secure transport
- encryption in transit
- HSTS
- mTLS
- TLS termination
- mixed content
- certificate expired
- transport security debugging

## Source trace

- OWASP Transport Layer Protection Cheat Sheet
