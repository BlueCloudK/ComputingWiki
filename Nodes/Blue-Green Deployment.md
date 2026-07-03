# Blue-Green Deployment

Aliases: blue green release, triển khai blue-green

Type: Deployment / Operations

## Context / Ngữ cảnh

Blue-Green Deployment xuất hiện khi cần chuyển traffic giữa hai environment/version để giảm downtime và rollback nhanh.

## Boundary / Ranh giới

### Nó là gì

Blue-Green Deployment là strategy có hai environment tương đương: một live, một chuẩn bị version mới.

### Nó không phải là gì

Nó không tự giải quyết database migration phức tạp và không phù hợp nếu cost chạy đôi quá cao.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là deploy vào idle environment, verify, switch traffic, giữ old environment để rollback.

## Project Role / Vai trò trong dự án

Node này giúp release an toàn hơn khi cần cutover rõ ràng.

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

- [[Deployment Strategy]] vì blue-green là một strategy
- [[Rollback]] vì rollback thường là switch traffic về environment cũ

## Liên quan rộng

- Zero-downtime release

## Source trace

- Continuous Delivery
