# Kubelet

Aliases: Kubernetes node agent, kubelet

Type: Kubernetes

## Context / Ngữ cảnh

Kubelet xuất hiện khi node cần agent chạy Pod spec bằng container runtime và báo trạng thái về control plane.

## Boundary / Ranh giới

### Nó là gì

Kubelet là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Kubelet là pod sync, container runtime interface, health probe, node status và volume mount.

## Project Role / Vai trò trong dự án

Kubelet giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Kubelet decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Kubelet
- Failure note ghi rõ Kubelet ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Kubelet đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Kubelet không?
- Khi Kubelet fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Kubelet làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Kubelet nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Kubelet nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Kubelet trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability

## Keywords / Từ khóa tìm kiếm

- Kubelet
- Kubernetes node agent
- kubelet debugging
- kubelet design
- deployment config
- vận hành hạ tầng

## Source trace

- Kubernetes docs
