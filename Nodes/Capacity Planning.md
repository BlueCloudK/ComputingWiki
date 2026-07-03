# Capacity Planning

Aliases: capacity management, lập kế hoạch năng lực

Type: Requirement / Planning

## Context / Ngữ cảnh

Capacity Planning xuất hiện khi hệ thống cần chuẩn bị đủ tài nguyên để chịu tải hiện tại và tăng trưởng tương lai mà không vỡ latency, availability hoặc cost.

## Boundary / Ranh giới

### Nó là gì

Capacity Planning là quá trình ước lượng workload, resource demand, headroom và scaling plan dựa trên traffic, data volume, concurrency và growth.

### Nó không phải là gì

Nó không phải là tối ưu hiệu năng từng hàm, không phải mua thêm máy theo cảm giác, và không thay thế load testing hoặc monitoring.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đo nhu cầu, dự báo tăng trưởng, tính bottleneck và đặt buffer. Planning tốt liên kết load, utilization, saturation, autoscaling và ngưỡng cảnh báo.

## Project Role / Vai trò trong dự án

Capacity Planning giúp team biết khi nào cần scale, giới hạn hiện tại nằm ở đâu và chi phí tăng theo tải như thế nào. Nó giảm rủi ro quá tải vào launch, campaign hoặc peak hour.

## Output / Artifact nên có

- Workload estimate: request rate, concurrent user, data growth
- Capacity model hoặc headroom target
- Scaling trigger, overload behavior và monitoring threshold

## Decision Checklist / Câu hỏi kiểm tra

- Peak load và normal load hiện tại là bao nhiêu?
- Bottleneck chính là CPU, memory, DB, network hay third-party limit?
- Headroom cần giữ là bao nhiêu và vì sao?
- Khi vượt capacity thì degrade, queue hay reject?
- Chi phí scale có chấp nhận được không?

## Failure Modes / Cách nó gây lỗi

- Chỉ scale sau khi user đã gặp outage
- Dự báo theo average load và bỏ qua peak
- Thêm tài nguyên sai tầng vì không biết bottleneck thật
- Không có overload plan nên hệ thống sập dây chuyền

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần model phức tạp cho prototype chưa có traffic thật
- Dễ over-engineer nếu tối ưu capacity trước khi biết workload thực tế

## Gồm những gì

- [[Load]]
- [[Scalability]]
- [[Overload Handling]]

## Nối mạnh

- [[Nonfunctional Requirement]] vì capacity thường xuất phát từ throughput, latency hoặc availability target
- [[Monitoring]] vì capacity planning cần số liệu sử dụng và saturation
- [[Load Test]] vì giả định capacity cần được kiểm chứng dưới tải

## Liên quan rộng

- Cloud cost
- Incident prevention
- Launch readiness

## Source trace

- SRE Map / capacity planning
