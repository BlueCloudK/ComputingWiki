# Vertical Pod Autoscaler

Aliases: Vertical Pod Autoscaler, VPA, vertical pod autoscaler, tự scale tài nguyên pod

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

Vertical Pod Autoscaler là node bổ sung cho ComputingWiki về controller đề xuất hoặc chỉnh resource request cho pod.

## Boundary / Ranh giới

### Nó là gì

Vertical Pod Autoscaler dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới controller đề xuất hoặc chỉnh resource request cho pod.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Cloud and Infrastructure; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Vertical Pod Autoscaler là hiểu boundary, input/output, state và failure mode riêng của controller đề xuất hoặc chỉnh resource request cho pod.

## Project Role / Vai trò trong dự án

Vertical Pod Autoscaler giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Vertical Pod Autoscaler manifest/config
- Health, rollout hoặc resource setting liên quan
- Operational note cho monitor/debug/rollback

## Decision Checklist / Câu hỏi kiểm tra

- Vertical Pod Autoscaler ảnh hưởng scheduling, networking, storage hay security?
- Manifest có owner, resource và failure behavior rõ không?
- Có cách observe và rollback khi rollout lỗi không?

## Failure Modes / Cách nó gây lỗi

- Misconfig Vertical Pod Autoscaler làm workload không chạy, không nhận traffic hoặc mất quyền
- Thiếu limit/probe/policy làm lỗi lan sang node/service khác
- Không có rollout/rollback path làm incident kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Vertical Pod Autoscaler nếu app nhỏ chạy ổn bằng deployment đơn giản
- Dễ over-engineer nếu dùng Kubernetes object phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Pod]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Vertical Pod Autoscaler
- [[Capacity]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Vertical Pod Autoscaler

## Liên quan rộng

- Kubernetes operations
- Container platform
- Cloud infrastructure

## Keywords / Từ khóa tìm kiếm

- Vertical Pod Autoscaler
- VPA
- vertical pod autoscaler
- tự scale tài nguyên pod
- vertical
- autoscaler

## Source trace

- Kubernetes official docs
- CNCF Cloud Native Trail Map
