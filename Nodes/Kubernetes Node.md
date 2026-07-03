# Kubernetes Node

Aliases: Kubernetes Node, node Kubernetes, worker node, máy trong cluster

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

Kubernetes Node là node bổ sung cho ComputingWiki về machine vật lý hoặc VM chạy pod trong cluster.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Node dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới machine vật lý hoặc VM chạy pod trong cluster.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Cloud and Infrastructure; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Kubernetes Node là hiểu boundary, input/output, state và failure mode riêng của machine vật lý hoặc VM chạy pod trong cluster.

## Project Role / Vai trò trong dự án

Kubernetes Node giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Kubernetes Node manifest/config
- Health, rollout hoặc resource setting liên quan
- Operational note cho monitor/debug/rollback

## Decision Checklist / Câu hỏi kiểm tra

- Kubernetes Node ảnh hưởng scheduling, networking, storage hay security?
- Manifest có owner, resource và failure behavior rõ không?
- Có cách observe và rollback khi rollout lỗi không?

## Failure Modes / Cách nó gây lỗi

- Misconfig Kubernetes Node làm workload không chạy, không nhận traffic hoặc mất quyền
- Thiếu limit/probe/policy làm lỗi lan sang node/service khác
- Không có rollout/rollback path làm incident kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Kubernetes Node nếu app nhỏ chạy ổn bằng deployment đơn giản
- Dễ over-engineer nếu dùng Kubernetes object phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Cluster]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Kubernetes Node
- [[Kubelet]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Kubernetes Node

## Liên quan rộng

- Kubernetes operations
- Container platform
- Cloud infrastructure

## Keywords / Từ khóa tìm kiếm

- Kubernetes Node
- node Kubernetes
- worker node
- máy trong cluster
- kubernetes
- node

## Source trace

- Kubernetes official docs
- CNCF Cloud Native Trail Map
