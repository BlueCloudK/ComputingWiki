# Error Budget

Aliases: error budget, ngân sách lỗi

Type: Reliability / SRE

## Context / Ngữ cảnh

Error Budget xuất hiện khi service có SLO và team cần biết còn bao nhiêu “lỗi được phép” trong một time window trước khi reliability không còn đạt mục tiêu. Nó giúp cân bằng giữa release nhanh và ổn định sản phẩm.

## Boundary / Ranh giới

### Nó là gì

Error Budget là phần downtime/error/latency violation được phép theo SLO. Ví dụ SLO 99.9% availability trong 30 ngày nghĩa là service có khoảng 0.1% request/thời gian được phép lỗi trong window đó. Budget burn càng nhanh thì càng cần giảm risk release và tập trung sửa reliability.

### Nó không phải là gì

Error Budget không phải lý do để cố tình gây lỗi cho đủ quota. Nó cũng không phải metric độc lập nếu không có SLO/SLI rõ. Nếu SLO đo sai user impact, error budget cũng dẫn team tới quyết định sai.

## Core Mechanism / Cơ chế lõi

Team định nghĩa SLI/SLO, tính allowed bad events hoặc allowed downtime, rồi đo bad events thực tế theo window. Burn rate cho biết tốc độ tiêu budget. Nếu burn rate cao, alert hoặc policy có thể yêu cầu rollback, freeze release, giảm traffic, fix reliability hoặc điều tra incident.

## Project Role / Vai trò trong dự án

Error Budget biến tranh luận “deploy tiếp hay sửa ổn định” thành quyết định dựa trên số liệu. Khi budget còn nhiều, team có thể chấp nhận release risk vừa phải. Khi budget cạn hoặc burn nhanh, team nên ưu tiên giảm lỗi, rollback hoặc harden hệ thống.

## Output / Artifact nên có

- Error budget calculation từ SLO và SLI cụ thể
- Burn-rate dashboard theo window ngắn/dài
- Policy khi budget burn nhanh hoặc cạn: rollback, release freeze, reliability sprint
- Alert rule dựa trên burn rate thay vì ngưỡng đơn lẻ
- Review định kỳ: budget dùng vào incident nào, action item nào giảm burn

## Decision Checklist / Câu hỏi kiểm tra

- SLO/SLI nào tạo ra error budget này?
- Bad event được tính là gì: failed request, slow request, downtime hay stale data?
- Burn rate hiện tại có vượt ngưỡng cần alert không?
- Budget cạn thì team phải dừng release hay chỉ review?
- Incident nào tiêu budget nhiều nhất?
- Có route/user journey nào tiêu budget nhưng bị che bởi aggregate metric không?
- Budget policy có được product/engineering đồng thuận không?

## Failure Modes / Cách nó gây lỗi

- SLO sai làm budget còn dư dù user đang đau.
- Budget policy không có quyền lực nên burn rate chỉ là dashboard trang trí.
- Aggregate budget che lỗi ở một tenant/region/endpoint quan trọng.
- Burn-rate alert quá nhạy tạo noise hoặc quá chậm làm phát hiện muộn.
- Team dùng budget như quota để chấp nhận lỗi không cần thiết.
- Không review incident tiêu budget nên lỗi lặp lại.

## Khi nào chưa cần hoặc dễ over-engineer

- Service chưa có user thật có thể chưa cần error budget formal.
- Không nên tạo budget nếu SLO/SLI chưa đáng tin hoặc không có policy đi kèm.
- Không nên áp dụng cùng một budget cho mọi endpoint nếu user impact rất khác nhau.

## Gồm những gì

- [[Service Level Objective]]
- [[Risk]]

## Nối mạnh

- [[Service Level Objective]] vì error budget được tính trực tiếp từ SLO.
- [[Monitoring]] vì cần telemetry để đo burn rate và bad events.
- [[Alert]] vì burn-rate alert là cách dùng error budget trong vận hành.
- [[Incident]] vì incident thường tiêu error budget và tạo action item.
- [[Deployment Strategy]] vì budget còn/cạn ảnh hưởng rollout và release risk.

## Liên quan rộng

- Release governance
- Reliability trade-off
- Risk management
- Product engineering alignment

## Keywords / Từ khóa tìm kiếm

- Error Budget
- error budget
- ngân sách lỗi
- SLO budget
- burn rate
- error budget policy
- bad events
- availability budget
- reliability budget
- release freeze
- SLO burn
- budget exhausted
- error budget alert
- reliability tradeoff

## Source trace

- Google SRE Book
- SRE Workbook SLO chapters
