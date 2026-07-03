# Kubernetes

Aliases: K8s, Kubernetes

Type: Deployment / Operations

## Context / Ngữ cảnh

Kubernetes xuất hiện khi cần orchestrate containerized workloads nhiều service hoặc nhiều instance.

## Boundary / Ranh giới

### Nó là gì

Kubernetes là platform quản lý deployment, scheduling, service discovery, scaling và desired state cho containers.

### Nó không phải là gì

Nó không phải Docker, không tự làm app cloud-native, và có operational cost lớn.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là declare desired state qua API objects; control plane reconcile cluster về state đó.

## Project Role / Vai trò trong dự án

Node này hữu ích khi workload cần orchestration, nhưng có thể quá nặng cho app nhỏ.

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

- [[Docker]] vì Kubernetes thường chạy container images
- [[Deployment Strategy]] vì Kubernetes hỗ trợ rollout qua controller

## Liên quan rộng

- Container orchestration
- Platform engineering

## Source trace

- Kubernetes official docs
