# API Mesh Gateway

Aliases: API Mesh Gateway, mesh gateway

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

API Mesh Gateway xuất hiện khi hệ thống có nhiều API/service và cần một lớp gateway/mesh để điều phối routing, auth, traffic policy, observability hoặc service-to-service access.

## Boundary / Ranh giới

### Nó là gì

API Mesh Gateway là lớp gateway/proxy trong kiến trúc API/service mesh, giúp kiểm soát traffic vào/giữa service bằng policy, routing, retry, timeout, rate limit, telemetry hoặc mTLS tùy thiết kế.

### Nó không phải là gì

API Mesh Gateway không phải business service. Nó không nên chứa domain logic chính; nó nên xử lý cross-cutting concern ở boundary traffic.

## Core Mechanism / Cơ chế lõi

Gateway/proxy nhận request, match route/policy, xác thực/ủy quyền nếu cần, áp timeout/retry/rate limit, forward tới upstream service và ghi metric/log/trace.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế edge gateway, internal service mesh, API policy, multi-service routing hoặc debug request đi sai service/timeout/rate limit.

## Output / Artifact nên có

- Route/policy config
- Upstream service map
- Auth/rate limit/timeout rule
- Observability signal: log/metric/trace
- Rollback/change plan

## Decision Checklist / Câu hỏi kiểm tra

- Gateway nằm ở edge hay internal mesh?
- Policy nào áp ở gateway, policy nào nằm trong service?
- Route có version/canary không?
- Timeout/retry có gây retry storm không?
- Log/trace có đủ để debug request path không?

## Failure Modes / Cách nó gây lỗi

- Gateway chứa quá nhiều business logic.
- Route sai làm request tới service sai version.
- Retry/timeout config tạo cascading failure.
- Authz chỉ kiểm ở gateway nhưng service nội bộ vẫn cần boundary.
- Observability thiếu làm không trace được request.

## Khi nào chưa cần hoặc dễ over-engineer

- Monolith hoặc vài service nhỏ có thể dùng reverse proxy/API gateway đơn giản.
- Không nên thêm mesh phức tạp nếu team chưa cần service-to-service policy rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Gateway]] vì API Mesh Gateway mở rộng vai trò gateway trong hệ nhiều service.
- [[Reverse Proxy]] vì gateway thường là proxy điều phối request.
- [[Rate Limiting]] vì gateway thường áp rate limit.
- [[Timeout]] vì timeout là policy quan trọng ở gateway.
- [[Monitoring]] vì gateway là điểm quan sát traffic tốt.

## Liên quan rộng

- Service mesh
- Edge gateway
- API governance

## Keywords / Từ khóa tìm kiếm

- API Mesh Gateway
- mesh gateway
- service mesh gateway
- API routing
- traffic policy
- gateway observability
- API mesh gateway debugging

## Source trace

- Envoy documentation
- Kubernetes official docs
