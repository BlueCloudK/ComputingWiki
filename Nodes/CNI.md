# CNI

Aliases: CNI, Container Network Interface

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

CNI xuất hiện trong Kubernetes/container runtime khi pod/container cần được gán network, IP, route và policy để giao tiếp trong cluster.

## Boundary / Ranh giới

### Nó là gì

CNI là chuẩn/plugin interface cho container networking. Trong Kubernetes, CNI plugin chịu trách nhiệm thiết lập network namespace, IP address, route và thường cả network policy behavior.

### Nó không phải là gì

CNI không phải Service hoặc Ingress. Service/Ingress định nghĩa cách route traffic ở tầng Kubernetes; CNI cung cấp nền network cho pod.

## Core Mechanism / Cơ chế lõi

Kubelet/container runtime gọi CNI plugin khi pod được tạo/xóa. Plugin cấp IP, cấu hình interface/route và kết nối pod vào network backend như overlay, routing native hoặc cloud VPC integration.

## Project Role / Vai trò trong dự án

Dùng node này khi debug pod không có IP, pod-to-pod network lỗi, network policy không áp, DNS/service connectivity hoặc cluster networking sau khi cài plugin.

## Output / Artifact nên có

- CNI plugin name/version
- Pod CIDR/network config
- Network policy support note
- Node route/interface check
- Debug command/log checklist

## Decision Checklist / Câu hỏi kiểm tra

- Cluster đang dùng CNI plugin nào?
- Pod CIDR có conflict với mạng hiện có không?
- Node có route/interface đúng không?
- NetworkPolicy có được plugin hỗ trợ không?
- Lỗi xảy ra giữa pod-pod, pod-service hay pod-internet?

## Failure Modes / Cách nó gây lỗi

- Pod không được cấp IP.
- Pod-to-pod traffic fail giữa node khác nhau.
- NetworkPolicy tưởng đã áp nhưng plugin không hỗ trợ.
- CIDR conflict với VPC/LAN.
- MTU sai làm request lớn bị treo khó debug.

## Khi nào chưa cần hoặc dễ over-engineer

- Local single-node cluster có thể dùng default CNI đơn giản.
- Không nên đổi CNI production nếu chưa có rollback plan và hiểu impact networking.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Service]] vì Service connectivity phụ thuộc pod network hoạt động đúng.
- [[Kubelet]] vì kubelet/container runtime gọi CNI khi tạo pod.
- [[Network Segmentation]] vì CNI/network policy liên quan segmentation trong cluster.
- [[Managed Kubernetes]] vì provider thường gắn CNI riêng với cloud networking.

## Liên quan rộng

- Kubernetes networking
- Pod network
- Network policy

## Keywords / Từ khóa tìm kiếm

- CNI
- Container Network Interface
- Kubernetes CNI
- pod network
- pod CIDR
- network policy
- CNI debugging

## Source trace

- Kubernetes official docs
- CNI specification
