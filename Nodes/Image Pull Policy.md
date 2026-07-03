# Image Pull Policy

Aliases: Image Pull Policy, imagePullPolicy, pull image policy, chính sách tải image

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

Image Pull Policy là node bổ sung cho ComputingWiki về policy quyết định Kubernetes pull image khi nào.

## Boundary / Ranh giới

### Nó là gì

Image Pull Policy dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới policy quyết định Kubernetes pull image khi nào.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Cloud and Infrastructure; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Image Pull Policy là hiểu boundary, input/output, state và failure mode riêng của policy quyết định Kubernetes pull image khi nào.

## Project Role / Vai trò trong dự án

Image Pull Policy giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Image Pull Policy manifest/config
- Health, rollout hoặc resource setting liên quan
- Operational note cho monitor/debug/rollback

## Decision Checklist / Câu hỏi kiểm tra

- Image Pull Policy ảnh hưởng scheduling, networking, storage hay security?
- Manifest có owner, resource và failure behavior rõ không?
- Có cách observe và rollback khi rollout lỗi không?

## Failure Modes / Cách nó gây lỗi

- Misconfig Image Pull Policy làm workload không chạy, không nhận traffic hoặc mất quyền
- Thiếu limit/probe/policy làm lỗi lan sang node/service khác
- Không có rollout/rollback path làm incident kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Image Pull Policy nếu app nhỏ chạy ổn bằng deployment đơn giản
- Dễ over-engineer nếu dùng Kubernetes object phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Container Image]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Image Pull Policy
- [[Kubernetes Pod]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Image Pull Policy

## Liên quan rộng

- Kubernetes operations
- Container platform
- Cloud infrastructure

## Keywords / Từ khóa tìm kiếm

- Image Pull Policy
- imagePullPolicy
- pull image policy
- chính sách tải image
- image
- pull
- policy

## Source trace

- Kubernetes official docs
- CNCF Cloud Native Trail Map
