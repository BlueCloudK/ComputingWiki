# TLS

Aliases: Transport Layer Security, bảo mật tầng vận chuyển

Type: Protocol / Data Format

## Context / Ngữ cảnh

TLS xuất hiện khi cần bảo vệ dữ liệu truyền qua network khỏi nghe lén, sửa đổi hoặc giả mạo.

## Boundary / Ranh giới

### Nó là gì

TLS là protocol tạo encrypted authenticated channel giữa peers.

### Nó không phải là gì

Nó không phải HTTP, user authentication, hay data-at-rest protection.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là handshake, certificate validation, key exchange và encrypted record layer.

## Project Role / Vai trò trong dự án

Node này giúp debug HTTPS, certificate, API security và transport protection.

## Output / Artifact nên có

- Certificate chain/config
- Protocol/cipher policy
- Renewal/expiry monitoring plan

## Decision Checklist / Câu hỏi kiểm tra

- Certificate có đúng hostname và chain không?
- TLS version/cipher có bị deprecated không?
- Client có verify certificate thay vì bỏ qua không?

## Failure Modes / Cách nó gây lỗi

- Cert hết hạn làm service down
- Tắt verification gây MITM risk
- Sai SNI/chain làm client fail

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần custom TLS policy nếu provider managed chuẩn
- Dễ over-engineer nếu chỉnh cipher khi không có compliance/threat requirement

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTPS]] vì HTTPS là HTTP chạy qua TLS
- [[Transport Layer Protection]] vì TLS là control chính

## Liên quan rộng

- Certificates
- Encryption in transit

## Source trace

- Computer Networks Map
- OWASP Transport Layer Protection
