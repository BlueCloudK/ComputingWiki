# HTTPS

Aliases: HTTP over TLS, HTTPS

Type: Protocol / Data Format

## Context / Ngữ cảnh

HTTPS xuất hiện khi web/API traffic cần HTTP semantics trên kênh TLS bảo mật.

## Boundary / Ranh giới

### Nó là gì

HTTPS là HTTP chạy qua TLS để bảo vệ channel truyền tải.

### Nó không phải là gì

Nó không phải security toàn diện cho API.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là HTTP request/response được truyền qua TLS connection đã xác thực certificate.

## Project Role / Vai trò trong dự án

Node này giúp đọc browser/API errors, mixed content, redirect và cert problems.

## Output / Artifact nên có

- HTTPS endpoint và redirect policy
- HSTS/mixed-content note nếu là web
- Certificate ownership/renewal note

## Decision Checklist / Câu hỏi kiểm tra

- Endpoint có enforce HTTPS không?
- Redirect HTTP sang HTTPS có đúng không?
- Secret có bị đặt trong URL/query log không?

## Failure Modes / Cách nó gây lỗi

- Mixed content làm browser block
- HTTP endpoint còn mở làm leak token
- Redirect loop vì proxy/TLS config sai

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần phức tạp cho local-only prototype
- Dễ over-engineer nếu mọi internal call đều cần public TLS stack riêng

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[HTTP]] vì HTTPS giữ HTTP semantics
- [[TLS]] vì TLS cung cấp encrypted channel

## Liên quan rộng

- Web security

## Source trace

- Computer Networks Map
- OWASP Cheat Sheet Series
