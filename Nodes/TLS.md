# TLS

Aliases: Transport Layer Security, bảo mật tầng vận chuyển, SSL successor, bảo mật tầng truyền tải

Type: Protocol / Data Format

## Context / Ngữ cảnh

TLS xuất hiện khi hai peer trên network cần tạo kênh truyền được mã hóa và xác thực. Nó là nền của HTTPS, mTLS, secure database connection, webhook security, service-to-service traffic và nhiều protocol bảo vệ dữ liệu in transit.

## Boundary / Ranh giới

### Nó là gì

TLS là protocol tạo encrypted authenticated channel giữa client và server. Nó dùng handshake, certificate, key exchange và symmetric encryption để chống nghe lén, sửa đổi dữ liệu và giả mạo server/peer trong quá trình truyền.

### Nó không phải là gì

TLS không phải HTTP, không phải user authentication đầy đủ và không bảo vệ dữ liệu khi đã nằm ở server/client. TLS cũng không cứu được API nếu certificate verification bị tắt, private key bị lộ, token bị log hoặc app thiếu authorization.

## Core Mechanism / Cơ chế lõi

TLS handshake thỏa thuận protocol version/cipher, server gửi certificate, client validate certificate chain/hostname, hai bên tạo shared secret qua key exchange, rồi dữ liệu application đi qua encrypted record layer. Với mTLS, client cũng trình certificate để server xác thực client.

## Project Role / Vai trò trong dự án

TLS là node cần mở khi debug certificate expired, wrong hostname, SNI, chain thiếu intermediate, client báo handshake failed, webhook không verify được, hoặc service nội bộ cần mTLS. Nó giúp team biết lỗi nằm ở certificate, protocol/cipher, hostname/SNI, proxy termination hay client verification.

## Output / Artifact nên có

- Certificate config: domain/SAN, issuer, chain, private key owner, expiry
- TLS policy: minimum version, cipher baseline, certificate validation rule
- Renewal/expiry monitoring và rotation plan
- Termination map: CDN/LB/reverse proxy/app/service mesh
- Test command/checklist: cert chain, hostname, SNI, protocol version, mTLS client cert nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Certificate có đúng hostname/SAN và chain đầy đủ không?
- Client có verify certificate/hostname không?
- TLS version/cipher cũ có bị chặn theo policy không?
- Private key được bảo vệ và rotate thế nào?
- TLS terminate ở đâu và upstream traffic còn được bảo vệ không?
- Có cần mTLS để xác thực client/service không?
- Cert expiry có alert trước khi outage không?

## Failure Modes / Cách nó gây lỗi

- Cert hết hạn làm browser/API client từ chối kết nối.
- Sai hostname/SAN hoặc thiếu intermediate chain làm một số client fail.
- Tắt certificate verification mở đường MITM.
- SNI/proxy config sai làm server trả nhầm certificate.
- Private key lộ làm attacker có thể giả mạo endpoint nếu không revoke/rotate.
- Protocol/cipher legacy gây compliance/security risk hoặc client mới từ chối.

## Khi nào chưa cần hoặc dễ over-engineer

- Managed TLS ở CDN/cloud LB thường đủ cho nhiều web app, không cần tự chỉnh cipher sâu.
- Local-only prototype có thể dùng self-signed cert hoặc HTTP, nhưng không nên lẫn với production assumption.
- Không nên triển khai mTLS nếu chưa có lifecycle cho certificate issuance, rotation và revocation.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTPS]] vì HTTPS là HTTP chạy trên TLS.
- [[Transport Layer Protection]] vì TLS là control chính cho data in transit.
- [[Reverse Proxy]] vì TLS thường terminate tại reverse proxy/LB/CDN.
- [[Secret]] vì private key/certificate key là secret cần bảo vệ.
- [[Session Management]] vì session token phải truyền qua TLS/HTTPS để tránh bị nghe lén.

## Liên quan rộng

- Certificates
- Encryption in transit
- Network security
- mTLS

## Keywords / Từ khóa tìm kiếm

- TLS
- Transport Layer Security
- bảo mật tầng vận chuyển
- SSL successor
- TLS handshake
- certificate chain
- certificate validation
- SNI
- cipher suite
- mTLS
- TLS termination
- cert expired
- private key
- encryption in transit
- TLS debugging

## Source trace

- Computer Networks Map
- OWASP Transport Layer Protection Cheat Sheet
