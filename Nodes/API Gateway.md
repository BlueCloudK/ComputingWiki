# API Gateway

Aliases: gateway API, edge gateway, cổng API

Type: API / Infrastructure

## Context / Ngữ cảnh

API Gateway xuất hiện khi nhiều API/service cần một entrypoint tập trung cho client traffic. Nó thường nằm ở edge hoặc trước backend services để xử lý routing, authentication, authorization, rate limiting, TLS termination, protocol translation, observability và policy enforcement.

## Boundary / Ranh giới

### Nó là gì

API Gateway là lớp trung gian nhận request từ client, match route/policy, rồi chuyển request tới upstream service phù hợp. Nó có thể enforce cross-cutting concerns như auth, quota, timeout, header normalization, request/response transformation và logging trước khi request vào service bên trong.

### Nó không phải là gì

API Gateway không phải nơi chứa business logic chính của domain. Nó cũng không thay thế service mesh, load balancer hay reverse proxy trong mọi trường hợp, dù có thể chồng lấn một số chức năng. Nếu nhét quá nhiều logic app vào gateway, debug và ownership sẽ rất khó.

## Core Mechanism / Cơ chế lõi

Gateway xử lý request theo pipeline: route matching, policy check, authentication/authorization, rate limit/quota, transform nếu cần, chọn upstream, áp timeout/retry, rồi ghi log/metric/tracing. Khi gateway sai, lỗi thường xuất hiện như 401/403/404/429/502/504, routing nhầm service, timeout hoặc header/body bị transform sai.

## Project Role / Vai trò trong dự án

API Gateway ảnh hưởng tới cách client nhìn toàn bộ backend. Nó là nơi gom API boundary, security policy, traffic control và observability cho nhiều service. Khi thiết kế microservice hoặc public API, team phải quyết định policy nào ở gateway, policy nào trong service, và cách debug request từ edge tới upstream.

## Output / Artifact nên có

- Gateway route table: path/method/host tới upstream service
- Auth/rate limit policy: endpoint nào public, endpoint nào protected, quota theo user/API key/IP
- Timeout/retry/circuit behavior cho từng upstream quan trọng
- Request/response transformation rule nếu có
- Observability setup: access log, request id, tracing header, 4xx/5xx/latency metric
- Runbook cho lỗi 401/403/404/429/502/504 ở gateway

## Decision Checklist / Câu hỏi kiểm tra

- Gateway đang xử lý policy nào, service bên trong vẫn phải tự verify gì?
- Route matching có rõ host/path/method/version không?
- Auth ở gateway có truyền identity/claims xuống service an toàn không?
- Rate limit tính theo IP, user, tenant, API key hay route?
- Timeout/retry ở gateway có làm retry storm hoặc duplicate request không?
- Log/tracing có đủ để đi từ request bên ngoài tới upstream service không?
- Khi gateway down hoặc config sai, có rollback/canary/config validation không?

## Failure Modes / Cách nó gây lỗi

- Route sai làm request tới nhầm service hoặc trả 404 dù service thật vẫn chạy.
- Auth policy thiếu làm endpoint private bị public, hoặc quá chặt làm client hợp lệ bị 403.
- Rate limit cấu hình sai làm chặn nhầm user thật hoặc không chặn được abuse.
- Timeout/retry không khớp upstream làm tăng 502/504 hoặc tạo duplicate side effect.
- Gateway strip/mutate header làm service mất identity, trace id hoặc content negotiation.
- Gateway trở thành single point of failure nếu không có HA, rollout và monitoring tốt.

## Khi nào chưa cần hoặc dễ over-engineer

- Monolith nhỏ hoặc vài endpoint nội bộ có thể dùng reverse proxy/load balancer đơn giản trước.
- Không nên đưa business workflow vào gateway chỉ để “gom logic” vì sẽ làm policy và domain logic trộn lẫn.
- Nếu team chưa có nhiều service/client/public API, gateway phức tạp có thể tăng vận hành hơn giá trị nhận được.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Security]] vì gateway thường enforce auth, rate limit và traffic policy ở edge.
- [[Rate Limiting]] vì gateway là vị trí phổ biến để áp quota/burst control.
- [[Load Balancer]] vì gateway thường phối hợp hoặc chồng lấn với traffic distribution tới upstream.
- [[Reverse Proxy]] vì nhiều gateway được triển khai như reverse proxy có thêm policy layer.
- [[Timeout]] vì gateway timeout quyết định client thấy 504 hay service có đủ thời gian xử lý.

## Liên quan rộng

- Platform engineering
- Microservices
- Edge security
- Observability
- Production operations

## Keywords / Từ khóa tìm kiếm

- API Gateway
- gateway API
- edge gateway
- cổng API
- API gateway route
- gateway policy
- gateway auth
- gateway rate limit
- gateway timeout
- upstream service
- 502 gateway
- 504 gateway timeout
- API traffic control
- edge routing
- API observability

## Source trace

- AWS API Gateway documentation
- Envoy documentation
- Microsoft API gateway pattern
