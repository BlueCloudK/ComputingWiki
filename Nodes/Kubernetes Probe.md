# Kubernetes Probe

Aliases: Kubernetes Probe, Kubernetes probe, health probe, probe Kubernetes

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

Kubernetes Probe xuất hiện khi kubelet cần biết container còn sống, đã sẵn sàng nhận traffic hoặc đã khởi động xong. Probe ảnh hưởng trực tiếp tới restart behavior, rollout, service routing và khả năng debug Pod bị CrashLoopBackOff hoặc không nhận traffic.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Probe là cấu hình health check trong Pod spec. Ba loại chính là liveness probe để biết container có cần restart không, readiness probe để biết Pod có nên nhận traffic từ Service không, và startup probe để cho app khởi động chậm có thời gian trước khi liveness bắt đầu đánh fail.

### Nó không phải là gì

Kubernetes Probe không phải monitoring đầy đủ và không phải business test toàn diện. Probe chỉ trả lời câu hỏi vận hành cụ thể cho kubelet/Service. Nếu probe quá nặng hoặc phụ thuộc sai dependency, nó có thể tự gây restart loop hoặc kéo Pod khỏi traffic dù app vẫn phục hồi được.

## Core Mechanism / Cơ chế lõi

Kubelet gọi probe theo interval bằng HTTP, TCP hoặc exec command. Nếu liveness fail quá ngưỡng, kubelet restart container. Nếu readiness fail, Pod bị remove khỏi Service endpoints nên không nhận traffic. Nếu startup probe được cấu hình, liveness/readiness có thể chờ tới khi startup pass.

## Project Role / Vai trò trong dự án

Kubernetes Probe là node cần mở khi Pod restart liên tục, rollout stuck, Service không route tới Pod, app bị traffic trước khi warm xong hoặc deploy cắt request đang xử lý. Nó giúp team chọn đúng probe, timeout, threshold và endpoint behavior.

## Output / Artifact nên có

- Probe config: liveness/readiness/startup, path/port/command, interval, timeout, threshold
- Health endpoint contract tương ứng trong app
- Startup time và warmup dependency note
- Runbook cho CrashLoopBackOff, readiness never ready, rollout stuck và false restart
- Test/deploy check để verify probe behavior trong staging

## Decision Checklist / Câu hỏi kiểm tra

- Check này là liveness, readiness hay startup?
- Nếu check fail, kubelet nên restart container hay chỉ remove khỏi traffic?
- Probe endpoint có quá phụ thuộc database/third-party không?
- Timeout/period/failureThreshold có phù hợp startup time và GC/CPU spike không?
- Readiness có fail trước khi graceful shutdown để drain traffic không?
- Probe có bị auth/middleware/proxy chặn không?
- App có endpoint riêng cho health hay dùng endpoint user-facing nặng?

## Failure Modes / Cách nó gây lỗi

- Liveness phụ thuộc database làm DB chậm kéo theo restart hàng loạt Pod.
- Readiness quá lỏng làm Pod nhận traffic khi app chưa warm xong.
- Startup probe thiếu khiến app khởi động chậm bị kill trước khi sẵn sàng.
- Timeout quá ngắn gây false fail dưới CPU/GC spike.
- Probe endpoint bị auth/CORS/middleware chặn làm Pod không ready.
- Exec probe quá nặng hoặc gọi script chậm làm node/app thêm tải.

## Khi nào chưa cần hoặc dễ over-engineer

- App demo đơn giản có thể bắt đầu bằng readiness/liveness rất nhẹ.
- Không nên dùng cùng một endpoint nặng cho mọi loại probe.
- Không nên để liveness kiểm tra tất cả downstream; readiness/degraded state thường phù hợp hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Health Check]] vì probe là cách Kubernetes dùng health check để điều khiển Pod.
- [[Kubelet]] vì kubelet là thành phần thực thi probe và restart/remove endpoint.
- [[Pod]] vì probe nằm trong Pod/container spec.
- [[Kubernetes Service]] vì readiness quyết định Pod có nằm trong Service endpoints không.
- [[Deployment Strategy]] vì rollout phụ thuộc readiness và probe đúng.

## Liên quan rộng

- Kubernetes operations
- Container platform
- Rollout debugging
- Service reliability

## Keywords / Từ khóa tìm kiếm

- Kubernetes Probe
- Kubernetes probe
- health probe
- probe Kubernetes
- liveness probe
- readiness probe
- startup probe
- HTTP probe
- TCP probe
- exec probe
- CrashLoopBackOff
- readiness failed
- rollout stuck
- kubelet probe
- probe debugging

## Source trace

- Kubernetes probes documentation
