# Health Check

Aliases: Health Check, health check, readiness endpoint, kiểm tra sức khỏe

Type: Backend Engineering

## Context / Ngữ cảnh

Health Check xuất hiện khi orchestrator, load balancer, monitoring system hoặc operator cần biết service còn sống, đã sẵn sàng nhận traffic, hay đang degraded. Nó thường dùng trong Kubernetes probes, load balancer target health, uptime monitoring và deploy/rollback automation.

## Boundary / Ranh giới

### Nó là gì

Health Check là endpoint/probe hoặc command trả trạng thái sức khỏe của service. Nó có thể tách thành liveness để biết process có nên restart không, readiness để biết có nên nhận traffic không, và startup check để biết app đang khởi động chưa xong.

### Nó không phải là gì

Health Check không phải monitoring đầy đủ và không nên thay thế observability. Một endpoint `/health` trả 200 không chứng minh mọi feature đều chạy đúng. Health check cũng không nên quá nặng tới mức tự tạo tải hoặc phụ thuộc vào mọi downstream khiến service bị kill/restart sai.

## Core Mechanism / Cơ chế lõi

Probe gọi endpoint/command theo interval. Nếu fail quá ngưỡng, orchestrator hoặc load balancer có thể bỏ instance khỏi pool, restart container hoặc alert. Health check tốt phải phản ánh đúng trạng thái cần quyết định: alive, ready, degraded hoặc dependency critical/uncritical.

## Project Role / Vai trò trong dự án

Health Check là node cần mở khi deploy không nhận traffic, pod restart loop, load balancer gửi request vào instance chưa ready, hoặc monitoring xanh giả dù user lỗi. Nó giúp team thiết kế probe đúng với startup time, dependency readiness, graceful shutdown và traffic routing.

## Output / Artifact nên có

- Health endpoint contract: path, status code, response body, timeout
- Liveness/readiness/startup probe config nếu dùng Kubernetes
- Load balancer health check config: interval, threshold, path, expected status
- Dependency policy: dependency nào làm not ready, dependency nào chỉ degraded
- Test/runbook cho startup slow, dependency down, shutdown và false positive/negative

## Decision Checklist / Câu hỏi kiểm tra

- Đây là liveness, readiness hay startup check?
- Probe fail thì action là restart, remove from traffic hay chỉ alert?
- Health check có phụ thuộc database/cache/third-party không, và phụ thuộc nào là critical?
- Timeout/interval/failure threshold có phù hợp startup và traffic thật không?
- Trong graceful shutdown, readiness có chuyển fail trước khi process stop không?
- Response có đủ debug nhưng không lộ secret/internal detail không?
- Health check có bị cache/proxy/auth chặn sai không?

## Failure Modes / Cách nó gây lỗi

- Liveness check quá nhạy làm container bị restart khi dependency tạm chậm.
- Readiness check quá lỏng làm load balancer gửi traffic vào instance chưa warm/ready.
- Health check xanh giả vì chỉ trả 200 mà không kiểm tra dependency critical.
- Health check đỏ giả vì kiểm tra dependency không critical và kéo service khỏi traffic.
- Probe timeout quá ngắn gây restart loop dưới CPU/GC spike.
- Shutdown không đổi readiness trước nên request mới vẫn vào instance đang thoát.

## Khi nào chưa cần hoặc dễ over-engineer

- App local/prototype có thể dùng health check đơn giản.
- Không nên check mọi downstream trong liveness; liveness nên nói process còn phục hồi được không.
- Không nên expose health detail nhạy cảm cho public internet nếu không có access control phù hợp.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Monitoring]] vì health check là tín hiệu đơn giản, còn monitoring cần metric/log/traces đầy đủ.
- [[Kubernetes Probe]] vì Kubernetes dùng liveness/readiness/startup probes để điều khiển pod.
- [[Load Balancer]] vì LB dựa vào health check để chọn backend healthy.
- [[Deployment Strategy]] vì rollout/rollback phụ thuộc readiness đúng.
- [[Web Server]] vì web server/app server thường expose health endpoint.

## Liên quan rộng

- Service reliability
- Orchestration
- Uptime monitoring
- Graceful shutdown

## Keywords / Từ khóa tìm kiếm

- Health Check
- health check
- readiness endpoint
- kiểm tra sức khỏe
- liveness probe
- readiness probe
- startup probe
- health endpoint
- service health
- load balancer health check
- Kubernetes health check
- graceful shutdown readiness
- false positive health check
- health check debugging

## Source trace

- Kubernetes probes documentation
- Google SRE Book
