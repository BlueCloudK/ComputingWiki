# Readiness Probe

Aliases: Readiness Probe, readiness probe, kiểm tra sẵn sàng, nhận traffic

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

Readiness Probe là node bổ sung cho ComputingWiki về probe cho biết pod đã sẵn sàng nhận traffic chưa.

## Boundary / Ranh giới

### Nó là gì

Readiness Probe dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới probe cho biết pod đã sẵn sàng nhận traffic chưa.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Cloud and Infrastructure; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Readiness Probe là hiểu boundary, input/output, state và failure mode riêng của probe cho biết pod đã sẵn sàng nhận traffic chưa.

## Project Role / Vai trò trong dự án

Readiness Probe giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Readiness Probe manifest/config
- Health, rollout hoặc resource setting liên quan
- Operational note cho monitor/debug/rollback

## Decision Checklist / Câu hỏi kiểm tra

- Readiness Probe ảnh hưởng scheduling, networking, storage hay security?
- Manifest có owner, resource và failure behavior rõ không?
- Có cách observe và rollback khi rollout lỗi không?

## Failure Modes / Cách nó gây lỗi

- Misconfig Readiness Probe làm workload không chạy, không nhận traffic hoặc mất quyền
- Thiếu limit/probe/policy làm lỗi lan sang node/service khác
- Không có rollout/rollback path làm incident kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Readiness Probe nếu app nhỏ chạy ổn bằng deployment đơn giản
- Dễ over-engineer nếu dùng Kubernetes object phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Probe]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Readiness Probe
- [[Kubernetes Service]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Readiness Probe

## Liên quan rộng

- Kubernetes operations
- Container platform
- Cloud infrastructure

## Keywords / Từ khóa tìm kiếm

- Readiness Probe
- readiness probe
- kiểm tra sẵn sàng
- nhận traffic
- readiness
- probe

## Source trace

- Kubernetes official docs
- CNCF Cloud Native Trail Map
