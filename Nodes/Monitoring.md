# Monitoring

Aliases: metrics, dashboard, giám sát

Type: Reliability / SRE

## Context / Ngữ cảnh

Monitoring xuất hiện khi service có user thật, traffic thật hoặc dữ liệu quan trọng và team cần biết hệ thống đang khỏe hay đang hỏng trước khi user hoặc business bị ảnh hưởng nặng. Nó thường gồm metric, log, trace, dashboard, alert, SLO và runbook.

## Boundary / Ranh giới

### Nó là gì

Monitoring là cách biến trạng thái runtime thành tín hiệu có thể quan sát và hành động được. Nó trả lời các câu như: service có đang phục vụ user không, latency/error có tăng không, resource có gần cạn không, dependency nào đang lỗi và alert nào cần người xử lý ngay.

### Nó không phải là gì

Monitoring không phải nhiều dashboard cho đẹp. Nếu metric không gắn user impact, alert không actionable hoặc không có runbook, monitoring dễ thành noise. Monitoring cũng không thay thế testing; nó giúp phát hiện và phản ứng khi hệ thống thật đang chạy.

## Core Mechanism / Cơ chế lõi

Hệ thống phát sinh telemetry: metrics, logs, traces, events và health checks. Telemetry được thu thập, lưu, query, visualize và gắn alert rule. Monitoring tốt ưu tiên golden signals như latency, traffic, errors, saturation; sau đó gắn với SLO/error budget và incident response.

## Project Role / Vai trò trong dự án

Monitoring ảnh hưởng tới release, rollback, incident response và ưu tiên technical debt. Khi deploy hoặc vận hành production, team cần dashboard để biết version mới có lỗi không, alert nào đáng đánh thức người trực và metric nào chứng minh user journey chính còn hoạt động.

## Output / Artifact nên có

- Service dashboard: traffic, latency p50/p95/p99, error rate, saturation, dependency health
- Alert rule có owner, severity, threshold, runbook và expected action
- SLO/SLI cho user journey quan trọng
- Log/trace convention: request id, trace id, status, duration, error context
- Incident runbook và postmortem/action item cho lỗi lặp lại

## Decision Checklist / Câu hỏi kiểm tra

- User-visible reliability được đo bằng metric nào?
- Alert này có action rõ không hay chỉ tạo noise?
- Dashboard có tách lỗi app, dependency, network và resource saturation không?
- SLO/error budget có ảnh hưởng release/rollback không?
- Log có đủ context để debug nhưng không lộ secret/PII không?
- Có trace/request id để nối frontend, gateway, backend và database không?
- Sau incident có action item giảm recurrence không?

## Failure Modes / Cách nó gây lỗi

- Alert fatigue làm team bỏ qua tín hiệu thật.
- Dashboard chỉ có CPU/RAM nhưng thiếu latency/error/user impact.
- Alert ngưỡng sai làm báo động quá muộn hoặc quá nhiều false positive.
- Log thiếu request id/trace id làm incident khó nối giữa service.
- Metric high-cardinality quá mức làm monitoring cost tăng và query chậm.
- Health check xanh giả khiến monitoring báo ổn trong khi user flow chính lỗi.
- Postmortem không có action item nên lỗi lặp lại.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype chưa có user thật có thể dùng logs + health check + vài metric cơ bản.
- Không nên tạo quá nhiều dashboard/alert trước khi biết user journey và failure mode quan trọng.
- Không nên alert mọi metric; chỉ alert khi cần hành động kịp thời.

## Gồm những gì

- [[Alert]]
- [[Service Level Objective]]
- [[Incident]]

## Nối mạnh

- [[Health Check]] vì health check là một tín hiệu đơn giản trong monitoring.
- [[Service Level Objective]] vì SLO biến reliability thành mục tiêu đo được.
- [[Incident]] vì monitoring phải dẫn tới incident response khi user impact xảy ra.
- [[Logging]] vì log là tín hiệu cần thiết để debug sau khi alert nổ.
- [[Tracing]] vì trace giúp tìm latency/error đi qua service nào.

## Liên quan rộng

- Production reliability
- Incident management
- Observability
- Release governance

## Keywords / Từ khóa tìm kiếm

- Monitoring
- giám sát
- metrics
- dashboard
- alert
- SLO
- SLI
- error budget
- golden signals
- latency p95
- error rate
- saturation
- observability
- incident response
- monitoring debugging

## Source trace

- Google SRE Book
- SRE Workbook
