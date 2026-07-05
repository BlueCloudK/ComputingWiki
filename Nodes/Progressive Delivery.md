# Progressive Delivery

Aliases: Progressive Delivery, progressive rollout

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Progressive Delivery xuất hiện khi team muốn phát hành thay đổi theo từng bước nhỏ, đo signal thật rồi mới mở rộng traffic hoặc user exposure.

## Boundary / Ranh giới

### Nó là gì

Progressive Delivery là cách deploy/release có kiểm soát bằng canary, blue-green, feature flag, traffic shifting, metric gate và rollback tự động hoặc thủ công.

### Nó không phải là gì

Progressive Delivery không phải chỉ là deploy chậm hơn. Nó cần signal, threshold và decision rule rõ để giảm risk production.

## Core Mechanism / Cơ chế lõi

Pipeline deploy version mới cho một phần traffic/user, thu metric như error rate, latency, saturation hoặc business signal, rồi tiếp tục tăng traffic, pause hoặc rollback.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế canary release, feature flag rollout, deployment strategy hoặc release gate dựa trên monitoring.

## Output / Artifact nên có

- Rollout plan
- Traffic/user percentage step
- Metric gate
- Rollback rule
- Owner/on-call note

## Decision Checklist / Câu hỏi kiểm tra

- Rollout tăng traffic theo bước nào?
- Metric nào quyết định pass/fail?
- Sample traffic có đại diện không?
- Rollback tự động hay thủ công?
- Feature flag có tách deploy khỏi release không?

## Failure Modes / Cách nó gây lỗi

- Metric gate không bắt đúng user impact.
- Canary traffic quá ít nên không có signal.
- Rollout quá nhanh như deploy full.
- Rollback không tương thích database/config.
- Feature flag quên cleanup sau release.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ ít user có thể dùng rolling deploy và smoke test trước.
- Không nên thêm progressive rollout nếu monitoring chưa đủ tin.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Deployment Strategy]] vì progressive delivery là nhóm chiến lược rollout.
- [[Monitoring]] vì rollout decision dựa trên signal.
- [[Rollback]] vì rollback là nhánh xử lý khi gate fail.
- [[CD]] vì progressive delivery thường nằm trong pipeline release.

## Liên quan rộng

- Canary release
- Feature flag
- Traffic shifting
- Release safety

## Keywords / Từ khóa tìm kiếm

- Progressive Delivery
- progressive rollout
- canary release
- feature flag rollout
- traffic shifting
- metric gate
- progressive delivery debugging

## Source trace

- Continuous Delivery
- Google SRE Books
