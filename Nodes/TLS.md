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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

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
