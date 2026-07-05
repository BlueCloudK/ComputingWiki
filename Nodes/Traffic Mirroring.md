# Traffic Mirroring

Aliases: Traffic Mirroring, request mirroring

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Traffic Mirroring xuất hiện khi team muốn gửi bản sao traffic thật tới service mới hoặc environment shadow để quan sát behavior mà chưa ảnh hưởng response người dùng.

## Boundary / Ranh giới

### Nó là gì

Traffic Mirroring là kỹ thuật sao chép request từ production path sang target phụ. Response từ target phụ thường bị bỏ qua, chỉ dùng để đo log, metric, compatibility hoặc performance.

### Nó không phải là gì

Traffic Mirroring không phải canary release thật. Canary trả response cho một phần user; mirroring chỉ quan sát bản sao và không nên tạo side effect production.

## Core Mechanism / Cơ chế lõi

Proxy, gateway hoặc service mesh nhận request chính, forward tới upstream thật, đồng thời gửi bản sao sang mirror target. Mirror target cần xử lý idempotent/read-only hoặc sandbox side effect.

## Project Role / Vai trò trong dự án

Dùng node này khi test service mới, migration backend, API compatibility, performance under real-like traffic hoặc validate release trước khi canary.

## Output / Artifact nên có

- Mirror source/target config
- Traffic percentage hoặc filter
- Side effect isolation rule
- Metric/log comparison
- Stop/rollback rule

## Decision Checklist / Câu hỏi kiểm tra

- Request nào được mirror?
- Mirror target có thể tạo side effect không?
- Dữ liệu nhạy cảm có bị gửi sang môi trường không phù hợp không?
- Metric nào dùng để so sánh?
- Có giới hạn traffic/cost không?

## Failure Modes / Cách nó gây lỗi

- Mirror target ghi dữ liệu thật ngoài ý muốn.
- Nhân đôi traffic làm tăng cost/load.
- PII bị gửi sang môi trường chưa đủ bảo vệ.
- Response mirror bị hiểu nhầm là user-facing.
- So sánh metric không cùng context nên kết luận sai.

## Khi nào chưa cần hoặc dễ over-engineer

- Service nhỏ có staging test đủ thì chưa cần mirror traffic.
- Không nên mirror traffic khi chưa cô lập side effect và dữ liệu nhạy cảm.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Gateway]] vì gateway/proxy thường thực hiện request mirroring.
- [[Progressive Delivery]] vì mirroring là bước an toàn trước rollout thật.
- [[Monitoring]] vì mirroring cần metric/log để so sánh.
- [[Load Balancer]] vì traffic control thường nằm gần load balancer/proxy.

## Liên quan rộng

- Shadow testing
- Service migration
- Release validation

## Keywords / Từ khóa tìm kiếm

- Traffic Mirroring
- request mirroring
- shadow traffic
- shadow testing
- mirrored request
- service mesh mirroring
- traffic mirroring debugging

## Source trace

- Kubernetes official docs
- Envoy documentation
