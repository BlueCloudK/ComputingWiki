# Managed Kubernetes

Aliases: Managed Kubernetes, managed K8s

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Managed Kubernetes xuất hiện khi team muốn dùng Kubernetes nhưng để cloud provider quản lý một phần control plane, upgrade, availability và cluster lifecycle.

## Boundary / Ranh giới

### Nó là gì

Managed Kubernetes là dịch vụ Kubernetes do provider vận hành control plane và tích hợp với cloud networking, IAM, storage, load balancer và monitoring.

### Nó không phải là gì

Managed Kubernetes không làm app tự ổn định. Team vẫn chịu trách nhiệm workload, manifest, autoscaling, RBAC, network policy, cost và observability.

## Core Mechanism / Cơ chế lõi

Provider cung cấp API server/control plane. Team tạo node pool, cấu hình networking/IAM/addon, deploy workload, theo dõi capacity và upgrade policy.

## Project Role / Vai trò trong dự án

Dùng node này khi chọn platform deploy, so sánh self-hosted Kubernetes, debug cloud integration hoặc thiết kế production cluster.

## Output / Artifact nên có

- Cluster config
- Node pool sizing
- IAM/RBAC boundary
- Networking/storage addon note
- Upgrade/backup/cost policy

## Decision Checklist / Câu hỏi kiểm tra

- Provider quản lý phần nào, team quản lý phần nào?
- Node pool có đủ capacity và autoscaling không?
- IAM/RBAC có least privilege không?
- Upgrade version có plan không?
- Cost alert và backup có chưa?

## Failure Modes / Cách nó gây lỗi

- Tưởng managed nghĩa là không cần vận hành workload.
- Node pool thiếu capacity làm pod pending.
- Cloud IAM/RBAC lệch làm deploy fail.
- Upgrade cluster phá addon/workload.
- Cost tăng vì autoscaling hoặc load balancer bị quên.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ có thể dùng VM, container service hoặc PaaS đơn giản hơn.
- Không nên chọn Kubernetes nếu team chưa có nhu cầu orchestration thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Service]] vì managed cluster vẫn chạy Service/Pod/Controller.
- [[Kubernetes RBAC]] vì quyền trong cluster vẫn là boundary quan trọng.
- [[Ingress Controller]] vì public traffic thường đi qua ingress.
- [[Cloud Budget Alert]] vì managed cluster dễ phát sinh cost ẩn.

## Liên quan rộng

- Cloud platform
- Cluster operations
- Container orchestration

## Keywords / Từ khóa tìm kiếm

- Managed Kubernetes
- managed K8s
- EKS
- GKE
- AKS
- node pool
- Kubernetes upgrade
- managed Kubernetes debugging

## Source trace

- Kubernetes official docs
- Google Kubernetes Engine documentation
- Amazon EKS documentation
