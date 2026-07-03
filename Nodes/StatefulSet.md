# StatefulSet

Aliases: StatefulSet, stateful workload, workload có trạng thái

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

StatefulSet là node bổ sung cho ComputingWiki về controller Kubernetes cho workload cần identity và storage ổn định.

## Boundary / Ranh giới

### Nó là gì

StatefulSet dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới controller Kubernetes cho workload cần identity và storage ổn định.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Cloud and Infrastructure; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của StatefulSet là hiểu boundary, input/output, state và failure mode riêng của controller Kubernetes cho workload cần identity và storage ổn định.

## Project Role / Vai trò trong dự án

StatefulSet giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- StatefulSet manifest/config
- Health, rollout hoặc resource setting liên quan
- Operational note cho monitor/debug/rollback

## Decision Checklist / Câu hỏi kiểm tra

- StatefulSet ảnh hưởng scheduling, networking, storage hay security?
- Manifest có owner, resource và failure behavior rõ không?
- Có cách observe và rollback khi rollout lỗi không?

## Failure Modes / Cách nó gây lỗi

- Misconfig StatefulSet làm workload không chạy, không nhận traffic hoặc mất quyền
- Thiếu limit/probe/policy làm lỗi lan sang node/service khác
- Không có rollout/rollback path làm incident kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần StatefulSet nếu app nhỏ chạy ổn bằng deployment đơn giản
- Dễ over-engineer nếu dùng Kubernetes object phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Controller]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng StatefulSet
- [[Persistent Volume]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng StatefulSet

## Liên quan rộng

- Kubernetes operations
- Container platform
- Cloud infrastructure

## Keywords / Từ khóa tìm kiếm

- StatefulSet
- stateful workload
- workload có trạng thái
- statefulset

## Source trace

- Kubernetes official docs
- CNCF Cloud Native Trail Map
