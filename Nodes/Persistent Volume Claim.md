# Persistent Volume Claim

Aliases: Persistent Volume Claim, PVC, persistent volume claim, yêu cầu volume

Type: Cloud and Infrastructure

## Context / Ngữ cảnh

Persistent Volume Claim là node bổ sung cho ComputingWiki về request storage của workload tới persistent volume.

## Boundary / Ranh giới

### Nó là gì

Persistent Volume Claim dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới request storage của workload tới persistent volume.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Cloud and Infrastructure; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Persistent Volume Claim là hiểu boundary, input/output, state và failure mode riêng của request storage của workload tới persistent volume.

## Project Role / Vai trò trong dự án

Persistent Volume Claim giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Persistent Volume Claim manifest/config
- Health, rollout hoặc resource setting liên quan
- Operational note cho monitor/debug/rollback

## Decision Checklist / Câu hỏi kiểm tra

- Persistent Volume Claim ảnh hưởng scheduling, networking, storage hay security?
- Manifest có owner, resource và failure behavior rõ không?
- Có cách observe và rollback khi rollout lỗi không?

## Failure Modes / Cách nó gây lỗi

- Misconfig Persistent Volume Claim làm workload không chạy, không nhận traffic hoặc mất quyền
- Thiếu limit/probe/policy làm lỗi lan sang node/service khác
- Không có rollout/rollback path làm incident kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Persistent Volume Claim nếu app nhỏ chạy ổn bằng deployment đơn giản
- Dễ over-engineer nếu dùng Kubernetes object phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Persistent Volume]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Persistent Volume Claim
- [[StorageClass]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Persistent Volume Claim

## Liên quan rộng

- Kubernetes operations
- Container platform
- Cloud infrastructure

## Keywords / Từ khóa tìm kiếm

- Persistent Volume Claim
- PVC
- persistent volume claim
- yêu cầu volume
- persistent
- volume
- claim

## Source trace

- Kubernetes official docs
- CNCF Cloud Native Trail Map
