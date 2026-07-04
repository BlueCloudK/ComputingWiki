# Load Balancer

Aliases: LB, cân bằng tải, traffic load balancing

Type: Deployment / Operations

## Context / Ngữ cảnh

Load Balancer xuất hiện khi nhiều instance/service/backend cùng phục vụ một loại traffic và hệ thống cần phân phối request/connection tới backend còn healthy. Nó thường nằm trước web server, API service, microservice pool, Kubernetes service, cloud target group hoặc reverse proxy tier.

## Boundary / Ranh giới

### Nó là gì

Load Balancer là thành phần nhận traffic rồi chọn backend dựa trên algorithm, health check và routing rule. Nó có thể hoạt động ở layer 4 theo TCP/UDP connection hoặc layer 7 theo HTTP host/path/header/cookie. Một số load balancer cũng terminate TLS, giữ sticky session hoặc expose metrics.

### Nó không phải là gì

Load Balancer không sửa app chậm, query tệ hoặc readiness sai. Nếu tất cả backend đều quá tải, load balancer chỉ phân phối lỗi đều hơn. Nó cũng không thay thế autoscaling, backpressure, retry policy hoặc health check đúng.

## Core Mechanism / Cơ chế lõi

LB có listener nhận request/connection, rule chọn target group/upstream, health check loại backend unhealthy, algorithm như round-robin/least connections/weighted routing, rồi forward traffic. Các yếu tố quan trọng gồm timeout, connection draining, TLS/proxy headers, sticky session, retry và health threshold.

## Project Role / Vai trò trong dự án

Load Balancer là node cần mở khi deploy nhiều instance, rollout/rollback, HA, autoscaling hoặc debug 502/503/504. Nó giúp team trace traffic từ client → LB listener → routing rule → target group → backend health → app logs.

## Output / Artifact nên có

- Listener/routing rule: port, protocol, host/path/header, target group
- Backend pool/target group: instances, weights, health check, draining policy
- TLS/proxy header decision: termination point, X-Forwarded-For/Proto, Host
- Metric: healthy targets, request count, target latency, 4xx/5xx, connection count
- Runbook cho unhealthy target, uneven load, 502/503/504 và rollout stuck

## Decision Checklist / Câu hỏi kiểm tra

- Health check có phản ánh readiness thật không?
- LB chọn backend theo thuật toán nào và có sticky session không?
- Timeout của LB có khớp app/server timeout không?
- Khi backend bị remove, connection đang mở có được drain graceful không?
- TLS terminate ở LB hay backend, và app có nhận đúng forwarded headers không?
- Traffic routing theo host/path/header/weight có đúng deploy strategy không?
- Metric có tách lỗi LB tạo ra và lỗi backend trả về không?

## Failure Modes / Cách nó gây lỗi

- Health check xanh giả làm LB gửi traffic vào instance lỗi/chưa ready.
- Health check đỏ giả làm tất cả backend bị remove khỏi pool.
- Sticky session hoặc weight sai làm tải lệch nặng vào vài instance.
- LB timeout ngắn hơn app làm client thấy 504 trong khi app vẫn xử lý.
- TLS/forwarded header sai làm redirect loop hoặc app nghĩ request là HTTP.
- Connection draining thiếu làm deploy cắt request đang xử lý.
- Target group/route rule sai làm traffic vào service/version nhầm.

## Khi nào chưa cần hoặc dễ over-engineer

- Một instance nội bộ hoặc prototype có thể chưa cần LB riêng.
- Không nên thêm nhiều tầng LB/proxy nếu chưa có nhu cầu HA/routing/TLS rõ.
- Không nên dùng LB để che readiness/deploy bug thay vì sửa health check và graceful shutdown.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Health Check]] vì LB dựa vào health check để chọn backend healthy.
- [[Reverse Proxy]] vì reverse proxy layer 7 có thể làm load balancing tới upstream.
- [[Deployment Strategy]] vì rollout/canary/blue-green thường điều khiển traffic qua LB.
- [[Timeout]] vì LB timeout ảnh hưởng trực tiếp tới 502/503/504.
- [[Web Server]] vì LB thường gửi traffic tới web server/app server instances.

## Liên quan rộng

- Traffic routing
- High availability
- Cloud networking
- Production deployment

## Keywords / Từ khóa tìm kiếm

- Load Balancer
- LB
- cân bằng tải
- traffic load balancing
- traffic distribution
- target group
- backend pool
- listener rule
- health check
- load balancing algorithm
- round robin
- least connections
- sticky session
- connection draining
- load balancer debugging

## Source trace

- AWS Well-Architected Framework
- Cloud architecture documentation
