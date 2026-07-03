# Pod Disruption Budget

Aliases: Pod Disruption Budget, PDB, pod disruption budget, ngân sách gián đoạn pod

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

Pod Disruption Budget là node bổ sung cho ComputingWiki về policy giới hạn số pod có thể unavailable trong voluntary disruption.

## Boundary / Ranh giới

### Nó là gì

Pod Disruption Budget dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới policy giới hạn số pod có thể unavailable trong voluntary disruption.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Cloud and Infrastructure; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Pod Disruption Budget là hiểu boundary, input/output, state và failure mode riêng của policy giới hạn số pod có thể unavailable trong voluntary disruption.

## Project Role / Vai trò trong dự án

Pod Disruption Budget giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Pod Disruption Budget manifest/config
- Health, rollout hoặc resource setting liên quan
- Operational note cho monitor/debug/rollback

## Decision Checklist / Câu hỏi kiểm tra

- Pod Disruption Budget ảnh hưởng scheduling, networking, storage hay security?
- Manifest có owner, resource và failure behavior rõ không?
- Có cách observe và rollback khi rollout lỗi không?

## Failure Modes / Cách nó gây lỗi

- Misconfig Pod Disruption Budget làm workload không chạy, không nhận traffic hoặc mất quyền
- Thiếu limit/probe/policy làm lỗi lan sang node/service khác
- Không có rollout/rollback path làm incident kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Pod Disruption Budget nếu app nhỏ chạy ổn bằng deployment đơn giản
- Dễ over-engineer nếu dùng Kubernetes object phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Deployment]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Pod Disruption Budget
- [[Reliability]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Pod Disruption Budget

## Liên quan rộng

- Kubernetes operations
- Container platform
- Cloud infrastructure

## Keywords / Từ khóa tìm kiếm

- Pod Disruption Budget
- PDB
- pod disruption budget
- ngân sách gián đoạn pod
- disruption
- budget

## Source trace

- Kubernetes official docs
- CNCF Cloud Native Trail Map
