# Cloud Computing

Aliases: cloud, điện toán đám mây

Type: Deployment / Operations

## Context / Ngữ cảnh

Cloud Computing xuất hiện khi hệ thống chạy trên tài nguyên được cung cấp qua cloud provider thay vì chỉ server tự quản lý.

## Boundary / Ranh giới

### Nó là gì

Cloud Computing là mô hình dùng compute, storage, network, managed service và identity qua API/self-service với khả năng scale và quản trị theo resource.

### Nó không phải là gì

Nó không phải tự động rẻ hơn, không tự động reliable hơn, và không thay thế việc hiểu architecture, security, cost và operations.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là tài nguyên hạ tầng trở thành service có lifecycle: provision, configure, secure, monitor, scale và decommission.

## Project Role / Vai trò trong dự án

Cloud Computing giúp deploy nhanh và dùng managed service, nhưng cũng tạo rủi ro về IAM, network, cost, vendor coupling và environment drift.

## Output / Artifact nên có

- Cloud resource inventory
- Environment/network/security boundary note
- Cost và reliability assumption

## Decision Checklist / Câu hỏi kiểm tra

- Workload cần compute/storage/network/service nào?
- Region/availability/cost requirement là gì?
- IAM và secret boundary đã rõ chưa?
- Managed service có lock-in hoặc operational trade-off gì?
- Resource có được quản lý bằng IaC không?

## Failure Modes / Cách nó gây lỗi

- Cloud bill tăng vì resource bỏ quên hoặc scale sai
- IAM quá rộng làm lộ quyền production
- Region/service dependency không có failure plan
- Manual config drift làm staging khác production

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần cloud nếu app chỉ chạy local hoặc một VPS đơn giản là đủ
- Dễ over-engineer nếu dùng quá nhiều managed service trước khi workload rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Infrastructure as Code]] vì cloud resource nên được mô tả và quản lý có version
- [[Deployment]] vì cloud là môi trường phổ biến để deploy service
- [[Monitoring]] vì cloud workload cần observability và cost visibility

## Liên quan rộng

- Regions
- Managed services
- IAM
- Cloud cost

## Keywords / Từ khóa tìm kiếm

- Cloud Computing
- cloud
- điện toán đám mây
- computing
- Deployment
- Operations
- điện toán
- cloud infrastructure
- hạ tầng cloud
- devops

## Source trace

- AWS Well-Architected Framework
- Google Cloud Architecture Framework
- Azure Architecture Center
