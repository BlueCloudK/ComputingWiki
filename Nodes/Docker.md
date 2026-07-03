# Docker

Aliases: container runtime/tooling, Docker, container runtime, docker container, container hóa

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

- Dockerfile
- Image tag/digest policy
- Runtime user/port/env note
- Build context và secret handling

## Decision Checklist / Câu hỏi kiểm tra

- Image có chứa secret hoặc file thừa không?
- Container chạy user nào?
- Image có reproducible và scan được không?

## Failure Modes / Cách nó gây lỗi

- Bake secret vào image layer
- Chạy root không cần thiết
- Dev image khác production image

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Docker nếu deploy/runtime đã đơn giản và ổn định
- Dễ over-engineer nếu container hóa che lấp config/runtime problem

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Container]] vì Docker hiện thực container workflow
- [[Kubernetes]] vì Kubernetes thường chạy container images

## Liên quan rộng

- Container images
- Dev environment

## Keywords / Từ khóa tìm kiếm

- Docker
- container image
- Dockerfile
- container runtime
- image build
- container registry
- Docker Compose
- container hóa
- đóng gói ứng dụng

## Source trace

- Docker official docs
