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

- Rollout plan: rolling, blue-green, canary
- Verification và rollback rule
- Traffic/exposure schedule

## Decision Checklist / Câu hỏi kiểm tra

- Downtime có chấp nhận không?
- Metric nào quyết định continue/rollback?
- Database/config change có backward compatible không?

## Failure Modes / Cách nó gây lỗi

- Deploy all-at-once không rollback được
- Rollout tiếp dù error tăng
- Strategy đẹp nhưng migration phá rollback

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần strategy phức tạp cho service không critical
- Dễ over-engineer nếu traffic thấp và manual deploy an toàn đủ

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
