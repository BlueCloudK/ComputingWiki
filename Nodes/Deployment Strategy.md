# Deployment Strategy

Aliases: deployment strategy, chiến lược triển khai

Type: Deployment / Operations

## Context / Ngữ cảnh

Deployment Strategy xuất hiện khi cần đưa version mới ra môi trường thật với downtime, blast radius và rollback risk được kiểm soát. Nó đặc biệt quan trọng khi service có nhiều user, nhiều instance, database migration, config change hoặc dependency change đi kèm release.

## Boundary / Ranh giới

### Nó là gì

Deployment Strategy là cách expose version mới ra traffic: recreate, rolling update, blue-green, canary, shadow traffic hoặc progressive delivery. Strategy quyết định thứ tự rollout, phần trăm traffic, verification gate, rollback trigger và cách xử lý instance cũ/mới cùng tồn tại.

### Nó không phải là gì

Deployment Strategy không phải toàn bộ CI/CD. CI/CD bao gồm build, test, package, deploy automation; deployment strategy chỉ là cách rollout version. Nó cũng không thay thế monitoring, backward compatibility, health check, rollback và migration planning.

## Core Mechanism / Cơ chế lõi

Rollout đưa version mới vào một phần hoặc toàn bộ backend pool, dùng health check/metrics/logs để verify, rồi tiếp tục tăng exposure hoặc rollback. Strategy an toàn cần readiness đúng, connection draining, backward-compatible API/database changes, config compatibility và metric gate như error rate/latency/business KPI.

## Project Role / Vai trò trong dự án

Deployment Strategy giúp team release mà không biến mỗi deploy thành gamble. Khi review release, cần biết downtime có chấp nhận không, user nào sẽ thấy version mới, metric nào cho phép tiếp tục, rollback có thật sự quay lại được không và database/config change có phá version cũ không.

## Output / Artifact nên có

- Rollout plan: strategy, traffic/exposure schedule, owner, window
- Verification gate: health check, smoke test, SLO metric, error/latency threshold
- Rollback plan: trigger, command, data/config compatibility, expected time
- Migration compatibility note nếu schema/config đổi
- Runbook cho rollout stuck, canary fail, health check fail và rollback fail

## Decision Checklist / Câu hỏi kiểm tra

- Downtime có chấp nhận được không?
- Version cũ và mới có chạy song song được không?
- Database migration/config change có backward compatible không?
- Metric nào quyết định continue, pause hoặc rollback?
- Health check/readiness có phản ánh instance thật sự ready không?
- Connection draining có tránh cắt request đang xử lý không?
- Rollback có bị phá bởi migration hoặc side effect không?

## Failure Modes / Cách nó gây lỗi

- Deploy all-at-once làm toàn bộ user gặp lỗi trước khi phát hiện.
- Rollout tiếp dù error rate/latency đã tăng vì không có gate rõ.
- Health check xanh giả làm version lỗi nhận traffic.
- Migration không backward compatible làm rollback app code cũng không cứu được.
- Blue-green/canary dùng cache/session không tương thích làm user thấy behavior lẫn lộn.
- Không drain connection khi replace instance làm request đang xử lý bị cắt.

## Khi nào chưa cần hoặc dễ over-engineer

- Service không critical, traffic thấp và rollback thủ công nhanh có thể chưa cần canary/blue-green phức tạp.
- Không nên làm strategy đẹp nếu monitoring và health check chưa đủ tin.
- Không nên chọn canary nếu traffic quá ít để metric canary có ý nghĩa thống kê.

## Gồm những gì

- [[Blue-Green Deployment]]
- [[Canary Release]]

## Nối mạnh

- [[Deployment]] vì strategy là cách triển khai version cụ thể.
- [[Rollback]] vì strategy phải có đường quay lại rõ.
- [[Health Check]] vì rollout dựa vào readiness/liveness đúng.
- [[Load Balancer]] vì nhiều strategy điều khiển traffic qua LB/target group.
- [[Monitoring]] vì metric quyết định rollout tiếp hay rollback.

## Liên quan rộng

- Rolling deployment
- Progressive delivery
- Release governance
- Change management

## Keywords / Từ khóa tìm kiếm

- Deployment Strategy
- deployment strategy
- chiến lược triển khai
- release strategy
- rollout plan
- rollback plan
- deployment risk
- progressive delivery
- rolling update
- blue green deployment
- canary release
- shadow traffic
- deployment verification
- connection draining
- deployment strategy debugging

## Source trace

- Continuous Delivery
- Google SRE Books
