# Alert

Aliases: alert, cảnh báo

Type: Reliability / SRE

## Context / Ngữ cảnh

Alert xuất hiện khi hệ thống cần gọi người hoặc automation vào xử lý vì một tín hiệu runtime cho thấy user impact, risk hoặc sự cố sắp xảy ra. Nó thường dựa trên metric, log, trace, health check, SLO burn rate hoặc synthetic check.

## Boundary / Ranh giới

### Nó là gì

Alert là rule biến tín hiệu quan sát được thành thông báo có action rõ cho owner phù hợp. Alert tốt phải trả lời: chuyện gì đang hỏng, impact là gì, độ khẩn cấp ra sao, ai xử lý, và bước đầu tiên nên làm gì.

### Nó không phải là gì

Alert không phải dashboard và không phải mọi metric vượt ngưỡng đều nên đánh thức người. Nếu alert không actionable, không gắn user impact hoặc quá nhiều false positive, nó tạo alert fatigue và làm team bỏ qua tín hiệu thật.

## Core Mechanism / Cơ chế lõi

Alert rule theo dõi condition như error rate, latency, saturation, SLO burn rate, queue lag hoặc health check failure. Khi condition giữ đủ lâu hoặc vượt threshold, hệ thống gửi notification tới channel/on-call. Alert cần severity, routing, deduplication, silence, escalation và runbook.

## Project Role / Vai trò trong dự án

Alert giúp team phản ứng kịp khi production có lỗi thật. Khi thiết kế monitoring, alert là nơi quyết định tín hiệu nào đáng gọi người, tín hiệu nào chỉ nên hiện dashboard, và tín hiệu nào nên trigger automation như rollback hoặc scale.

## Output / Artifact nên có

- Alert rule: metric/query, threshold, duration, severity, owner
- Runbook link: cách xác minh, giảm impact, rollback/escalate
- Routing/escalation policy: channel, on-call, business hours hay 24/7
- Noise review: false positive, duplicate, flapping, silence condition
- Post-incident tuning nếu alert quá muộn, quá sớm hoặc không nổ

## Decision Checklist / Câu hỏi kiểm tra

- Alert này có user impact hoặc risk rõ không?
- Người nhận alert có action cụ thể trong vài phút đầu không?
- Threshold/duration có tránh flapping và false positive không?
- Severity có đúng mức cần đánh thức người không?
- Alert có runbook và owner không?
- Có cần alert theo SLO burn rate thay vì một metric đơn lẻ không?
- Sau incident, alert này đã nổ đúng lúc chưa?

## Failure Modes / Cách nó gây lỗi

- Alert quá nhiều làm alert fatigue và team bỏ qua sự cố thật.
- Alert không actionable khiến người trực chỉ nhìn dashboard nhưng không biết làm gì.
- Threshold quá cao làm báo động khi user đã bị ảnh hưởng lâu.
- Threshold quá thấp làm false positive liên tục.
- Alert thiếu routing/owner nên không ai xử lý.
- Alert chỉ nhìn health check xanh giả nên bỏ sót lỗi user journey chính.

## Khi nào chưa cần hoặc dễ over-engineer

- Service chưa có user thật có thể bắt đầu bằng log/metric/dashboard trước khi on-call alert nặng.
- Không nên alert mọi warning; chỉ alert khi cần hành động kịp thời.
- Không nên tạo alert nếu chưa có runbook hoặc owner chịu trách nhiệm.

## Gồm những gì

- [[Monitoring]]
- [[Incident Response]]

## Nối mạnh

- [[Monitoring]] vì alert là phần actionable của monitoring.
- [[Service Level Objective]] vì SLO/burn rate thường là nền cho alert ít noise hơn.
- [[Incident]] vì alert thường là điểm mở incident.
- [[Health Check]] vì health check failure có thể trigger alert nếu ảnh hưởng traffic.
- runbook vì alert cần hướng dẫn xử lý ban đầu.

## Liên quan rộng

- On-call
- Incident management
- Alert fatigue
- Reliability operations

## Keywords / Từ khóa tìm kiếm

- Alert
- cảnh báo
- alert rule
- alert fatigue
- actionable alert
- false positive alert
- SLO burn rate
- on-call alert
- escalation policy
- alert routing
- runbook
- incident alert
- monitoring alert
- alert flapping
- alert debugging

## Source trace

- Google SRE Book
- SRE Workbook alerting guidance
