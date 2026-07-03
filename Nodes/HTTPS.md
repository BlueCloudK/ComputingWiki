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

- [[HTTP]] vì HTTPS giữ HTTP semantics
- [[TLS]] vì TLS cung cấp encrypted channel

## Liên quan rộng

- Web security

## Source trace

- Computer Networks Map
- OWASP Cheat Sheet Series
