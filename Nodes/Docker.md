# Docker

Aliases: container runtime/tooling, Docker

Type: Deployment / Operations

## Context / Ngữ cảnh

Docker xuất hiện khi cần đóng gói app và dependency thành container image chạy nhất quán hơn giữa môi trường.

## Boundary / Ranh giới

### Nó là gì

Docker là tooling/container platform để build, ship và run container images.

### Nó không phải là gì

Nó không phải VM đầy đủ, không tự bảo mật app, và không thay thế deployment strategy.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là image layers, container filesystem/process isolation và registry distribution.

## Project Role / Vai trò trong dự án

Node này giúp reproducible dev/deploy và giảm lệch dependency giữa môi trường.

## Output / Artifact nên có

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Container]] vì Docker hiện thực container workflow
- [[Kubernetes]] vì Kubernetes thường chạy container images

## Liên quan rộng

- Container images
- Dev environment

## Source trace

- Docker official docs
