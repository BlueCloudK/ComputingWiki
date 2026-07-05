# Dashboard

Aliases: Dashboard, operational dashboard

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Dashboard xuất hiện khi team cần quan sát nhanh trạng thái hệ thống, service, pipeline, cost, incident hoặc SLO bằng metric/log/event đã được chọn lọc.

## Boundary / Ranh giới

### Nó là gì

Dashboard là giao diện tổng hợp signal quan trọng để trả lời câu hỏi vận hành cụ thể: hệ thống có ổn không, lỗi nằm ở đâu, xu hướng đang xấu đi không.

### Nó không phải là gì

Dashboard không phải bãi nhồi mọi metric. Nếu không gắn với câu hỏi/debug path, dashboard dễ đẹp nhưng không giúp ra quyết định.

## Core Mechanism / Cơ chế lõi

Dashboard lấy dữ liệu từ monitoring/log/tracing/cost system, query thành panel, group theo service/environment và dùng threshold/annotation để giúp đọc biến động theo thời gian.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế observability, incident triage, release monitoring, SLO review, cost review hoặc executive/status view.

## Output / Artifact nên có

- Dashboard purpose
- Panel list and query
- Service/environment filters
- Threshold/annotation rule
- Owner and review cadence

## Decision Checklist / Câu hỏi kiểm tra

- Dashboard trả lời câu hỏi nào?
- Metric/log nào là signal chính?
- Có phân biệt service/environment/version không?
- Panel có threshold hoặc baseline không?
- Dashboard có owner giữ cho không stale không?

## Failure Modes / Cách nó gây lỗi

- Quá nhiều panel làm người xem không biết nhìn đâu.
- Metric không gắn với user impact.
- Dashboard stale sau khi service đổi tên/metric đổi.
- Chỉ có dashboard, không có alert khi người không nhìn màn hình.
- Panel đẹp nhưng không giúp debug bước tiếp theo.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ có thể bắt đầu bằng vài metric/alert cơ bản.
- Không nên build dashboard trước khi biết câu hỏi vận hành thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Monitoring]] vì dashboard hiển thị metric/signal từ monitoring.
- [[Alert]] vì dashboard và alert nên dùng cùng signal quan trọng.
- [[Service Level Objective]] vì dashboard nên thể hiện SLO/user impact.
- [[Cost Review]] vì cost dashboard hỗ trợ review chi phí.

## Liên quan rộng

- Observability
- Incident triage
- Metric visualization

## Keywords / Từ khóa tìm kiếm

- Dashboard
- operational dashboard
- monitoring dashboard
- SLO dashboard
- incident dashboard
- dashboard design
- dashboard debugging

## Source trace

- Google SRE Books
- OpenTelemetry documentation
- Grafana documentation
