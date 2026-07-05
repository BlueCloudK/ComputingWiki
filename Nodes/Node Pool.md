# Node Pool

Aliases: Node Pool, Kubernetes node pool

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Node Pool xuất hiện trong managed Kubernetes khi cluster có nhiều nhóm node với machine type, autoscaling, label, taint hoặc purpose khác nhau.

## Boundary / Ranh giới

### Nó là gì

Node Pool là nhóm node worker có cấu hình chung, thường cùng instance type, disk, autoscaling rule, zone/region và label/taint.

### Nó không phải là gì

Node Pool không phải namespace hay workload group. Namespace tổ chức object logic; node pool là capacity compute thật nơi pod được schedule.

## Core Mechanism / Cơ chế lõi

Cluster autoscaler hoặc cloud provider tạo/xóa node trong pool theo nhu cầu. Scheduler đặt pod lên node phù hợp dựa trên resource request, node selector, affinity, taint/toleration và constraint của workload.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế capacity cho cluster, tách workload GPU/CPU, isolate system/user workload, debug pod pending hoặc tối ưu chi phí node.

## Output / Artifact nên có

- Node pool config
- Machine type/disk/zone
- Label/taint rule
- Autoscaling min/max
- Workload placement policy

## Decision Checklist / Câu hỏi kiểm tra

- Workload nào nên chạy trên pool này?
- Resource request có khớp capacity node không?
- Taint/toleration có chặn pod ngoài ý muốn không?
- Autoscaling min/max có đủ peak không?
- Pool có làm chi phí tăng vì idle capacity không?

## Failure Modes / Cách nó gây lỗi

- Pod pending vì node selector/taint sai.
- Pool quá nhỏ hoặc instance type không hợp workload.
- Autoscaler không scale do request/constraint sai.
- Tách quá nhiều pool làm fragment capacity và tăng chi phí.
- System workload bị đặt chung với workload nặng gây nhiễu.

## Khi nào chưa cần hoặc dễ over-engineer

- Cluster nhỏ có thể bắt đầu với một pool chung.
- Không nên tạo nhiều node pool trước khi có workload placement/cost constraint rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Managed Kubernetes]] vì node pool thường là tính năng của managed cluster.
- [[Kubernetes Controller]] vì autoscaler/controller quản lý desired capacity.
- [[Resource Quota]] vì resource request/quota ảnh hưởng capacity planning.
- [[Limit Range]] vì limit/request default ảnh hưởng scheduling lên node pool.

## Liên quan rộng

- Cluster autoscaling
- Workload placement
- Compute capacity

## Keywords / Từ khóa tìm kiếm

- Node Pool
- Kubernetes node pool
- managed Kubernetes node pool
- taint toleration
- node selector
- cluster autoscaler
- node pool debugging

## Source trace

- Kubernetes official docs
- Google Kubernetes Engine documentation
- Amazon EKS documentation
