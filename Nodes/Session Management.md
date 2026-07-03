# Session Management

Aliases: session security, quản lý phiên

Type: Security

## Context / Ngữ cảnh

Session Management xuất hiện khi hệ thống cần duy trì trạng thái đăng nhập hoặc phiên làm việc an toàn.

## Boundary / Ranh giới

### Nó là gì

Session Management là practice tạo, lưu, rotate, expire và bảo vệ session/token sau authentication.

### Nó không phải là gì

Nó không phải authentication bản thân và không thay thế authorization.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là session identifier/token đủ ngẫu nhiên, truyền/lưu an toàn, expire đúng và revoke khi cần.

## Project Role / Vai trò trong dự án

Node này giúp tránh session hijacking, fixation và logout không hiệu lực.

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

- [[Authentication]] vì session bắt đầu sau khi xác thực
- [[Transport Layer Protection]] vì session token cần truyền qua kênh bảo mật

## Liên quan rộng

- Cookies
- Token lifecycle

## Source trace

- OWASP Session Management Cheat Sheet
