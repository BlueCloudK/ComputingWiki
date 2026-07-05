# Cloud Budget Alert

Aliases: Cloud Budget Alert, cloud cost alert

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Cloud Budget Alert xuất hiện khi cloud resource có thể phát sinh chi phí vượt dự kiến do autoscaling, storage growth, data transfer, managed service hoặc resource bị quên.

## Boundary / Ranh giới

### Nó là gì

Cloud Budget Alert là cảnh báo dựa trên budget, forecast hoặc actual cloud spend để phát hiện cost spike sớm.

### Nó không phải là gì

Cloud Budget Alert không tự tối ưu cost. Nó chỉ báo hiệu; team vẫn cần owner, investigation và action rõ.

## Core Mechanism / Cơ chế lõi

Cloud billing system theo dõi spend theo account/project/service/tag. Khi actual hoặc forecast vượt threshold, alert gửi tới kênh owner để review và xử lý.

## Project Role / Vai trò trong dự án

Dùng node này khi vận hành cloud, managed Kubernetes, storage, GPU/AI workload hoặc demo public có nguy cơ bị abuse cost.

## Output / Artifact nên có

- Budget threshold
- Forecast/actual alert rule
- Owner/channel
- Cost tag policy
- Response checklist

## Decision Checklist / Câu hỏi kiểm tra

- Budget áp cho account, project hay service nào?
- Threshold bao nhiêu phần trăm?
- Alert gửi tới ai?
- Resource có tag/label để truy cost không?
- Khi alert xảy ra thì tắt/giới hạn cái gì trước?

## Failure Modes / Cách nó gây lỗi

- Alert gửi sai người nên không ai xử lý.
- Budget chỉ báo sau khi cost đã vượt quá nhiều.
- Không có tag nên không biết service nào đốt tiền.
- Autoscaling/resource leak làm cost tăng âm thầm.
- Alert quá nhiều gây noise và bị ignore.

## Khi nào chưa cần hoặc dễ over-engineer

- Local-only hoặc free-tier test có thể chỉ cần manual check.
- Không nên tạo quá nhiều alert nhỏ nếu chưa có owner xử lý.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Managed Kubernetes]] vì cluster managed dễ phát sinh cost từ node/load balancer/storage.
- [[Monitoring]] vì budget alert là một dạng operational signal.
- [[Alert]] vì cần channel và threshold rõ.
- [[Resource Exhaustion]] vì resource runaway có thể gây cả cost spike lẫn outage.

## Liên quan rộng

- Cloud cost management
- FinOps
- Budget governance

## Keywords / Từ khóa tìm kiếm

- Cloud Budget Alert
- cloud cost alert
- budget threshold
- cost spike
- billing alert
- cloud spend forecast
- cloud budget debugging

## Source trace

- Google Cloud Billing documentation
- AWS Budgets documentation
