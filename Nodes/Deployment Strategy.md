# Deployment Strategy

Aliases: deployment strategy, chiến lược triển khai

Type: Deployment / Operations

## Context / Ngữ cảnh

Deployment Strategy xuất hiện khi cần đưa version mới ra môi trường thật với rủi ro kiểm soát được.

## Boundary / Ranh giới

### Nó là gì

Deployment Strategy là cách release traffic/version như rolling, blue-green, canary hoặc recreate.

### Nó không phải là gì

Nó không phải CI/CD toàn bộ và không thay thế monitoring/rollback.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là kiểm soát thứ tự rollout, exposure, verification và rollback.

## Project Role / Vai trò trong dự án

Node này giúp chọn cách deploy phù hợp với risk, downtime và observability.

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

- [[Blue-Green Deployment]]
- [[Canary Release]]

## Nối mạnh

- [[Deployment]] vì strategy là cách triển khai cụ thể
- [[Rollback]] vì strategy phải có đường quay lại

## Liên quan rộng

- Rolling deployment
- Progressive delivery

## Source trace

- Continuous Delivery
- Google SRE Books
