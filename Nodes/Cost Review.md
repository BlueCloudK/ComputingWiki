# Cost Review

Aliases: Cost Review, cloud cost review

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Cost Review xuất hiện khi cloud/resource cost cần được kiểm tra định kỳ hoặc trước/sau thay đổi hạ tầng để tránh chi phí tăng ngoài ý muốn.

## Boundary / Ranh giới

### Nó là gì

Cost Review là hoạt động phân tích chi phí theo service, workload, environment, owner hoặc change để phát hiện waste, anomaly và tradeoff giữa cost/performance/reliability.

### Nó không phải là gì

Cost Review không chỉ là nhìn tổng hóa đơn cuối tháng. Review tốt cần tag/owner, baseline, trend, forecast và action cụ thể.

## Core Mechanism / Cơ chế lõi

Team thu cost data, group theo tag/service/environment, so với baseline/budget, tìm resource idle/overprovisioned/anomaly, rồi chốt action như resize, lifecycle policy, reserved capacity hoặc alert.

## Project Role / Vai trò trong dự án

Dùng node này khi tối ưu chi phí cloud, review IaC PR có resource đắt, kiểm soát budget startup/lab hoặc debug bill tăng đột biến.

## Output / Artifact nên có

- Cost breakdown by service/tag
- Baseline and anomaly note
- Owner/action list
- Budget alert threshold
- Before/after saving estimate

## Decision Checklist / Câu hỏi kiểm tra

- Cost tăng từ service/resource nào?
- Resource có owner/tag rõ không?
- Usage có khớp provisioned capacity không?
- Có lifecycle/autoscaling/right-sizing chưa?
- Saving action có ảnh hưởng reliability/performance không?

## Failure Modes / Cách nó gây lỗi

- Không tag resource nên không biết team/service nào tạo cost.
- Chỉ tối ưu rẻ hơn nhưng làm giảm reliability.
- Idle resource, snapshot, log, object version cũ bị bỏ quên.
- Budget alert quá muộn sau khi cost đã tăng.
- Review chỉ một lần, không thành cadence vận hành.

## Khi nào chưa cần hoặc dễ over-engineer

- Lab rất nhỏ có thể bắt đầu bằng budget alert và tag cơ bản.
- Không nên spend nhiều effort FinOps nếu cost chưa đáng kể hoặc chưa có owner rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cloud Budget Alert]] vì alert giúp phát hiện cost vượt ngưỡng.
- [[Capacity Review]] vì capacity dư thường là nguồn cost waste.
- [[Object Lifecycle Policy]] vì lifecycle policy giúp giảm storage cost.
- [[Node Pool]] vì node pool sizing ảnh hưởng chi phí Kubernetes.

## Liên quan rộng

- FinOps
- Cost anomaly
- Resource tagging

## Keywords / Từ khóa tìm kiếm

- Cost Review
- cloud cost review
- cost anomaly
- cloud bill
- resource tagging
- right sizing
- cost review debugging

## Source trace

- Google Cloud cost management documentation
- AWS cost management documentation
- FinOps Foundation materials
