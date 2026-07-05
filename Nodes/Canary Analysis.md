# Canary Analysis

Aliases: Canary Analysis, canary analysis

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Canary Analysis xuất hiện khi version mới được rollout cho một phần nhỏ traffic/user và cần quyết định tiếp tục rollout hay rollback dựa trên metric thật.

## Boundary / Ranh giới

### Nó là gì

Canary Analysis là quá trình so sánh signal của canary version với baseline/stable version để đánh giá release mới có an toàn không.

### Nó không phải là gì

Canary Analysis không chỉ là “deploy ít traffic”. Nếu không có metric, threshold và decision rule, canary chỉ là rollout chậm hơn nhưng vẫn mù.

## Core Mechanism / Cơ chế lõi

Traffic được chia giữa stable và canary. Hệ thống thu metric như error rate, latency, saturation, crash, business conversion hoặc log anomaly, rồi so sánh với threshold để pass, pause hoặc rollback.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế progressive delivery, automated rollout gate, rollback rule hoặc debug vì sao release mới chỉ lỗi ở một phần traffic.

## Output / Artifact nên có

- Canary metric list
- Baseline comparison window
- Pass/fail threshold
- Rollback rule
- Owner/on-call context

## Decision Checklist / Câu hỏi kiểm tra

- Metric nào đại diện user impact?
- Canary traffic có đủ sample không?
- Baseline có cùng điều kiện traffic không?
- Threshold pass/fail là gì?
- Khi fail thì rollback tự động hay cần approval?

## Failure Modes / Cách nó gây lỗi

- Sample traffic quá ít nên không thấy lỗi.
- Metric chọn sai nên release lỗi vẫn pass.
- Baseline/canary khác loại user nên so sánh lệch.
- Rollout tăng quá nhanh trước khi signal ổn định.
- Alert noise làm người trực bỏ qua canary failure.

## Khi nào chưa cần hoặc dễ over-engineer

- Service nhỏ ít traffic có thể dùng smoke test và manual monitoring trước.
- Không nên tự động rollback nếu metric chưa đủ tin và dễ false positive.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Progressive Delivery]] vì canary analysis là gate quan trọng của progressive rollout.
- [[Monitoring]] vì analysis dựa trên metric/log thật.
- [[Rollback]] vì canary fail cần rollback nhanh.
- [[Service Level Objective]] vì threshold nên gắn với user-visible reliability.

## Liên quan rộng

- Canary release
- Metric gate
- Release safety

## Keywords / Từ khóa tìm kiếm

- Canary Analysis
- canary analysis
- canary release
- metric gate
- rollback threshold
- progressive rollout
- canary analysis debugging

## Source trace

- Google SRE Books
- Continuous Delivery
