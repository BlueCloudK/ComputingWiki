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

- Deployment manifest
- Service/Ingress config
- Resource request/limit và health check
- Rollout strategy

## Decision Checklist / Câu hỏi kiểm tra

- App có cần orchestration hay PaaS đơn giản đủ?
- Pod có request/limit và readiness/liveness chưa?
- Config/secret/volume được quản lý thế nào?

## Failure Modes / Cách nó gây lỗi

- Thiếu resource limit làm pod ăn hết node
- Readiness check sai làm traffic vào pod chưa sẵn sàng
- RBAC/secret misconfig làm lộ quyền

## Khi nào chưa cần hoặc dễ over-engineer

- Kubernetes overkill cho app nhỏ một service
- Dễ over-engineer nếu team chưa có năng lực vận hành cluster

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
