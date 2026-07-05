# Sidecar Proxy

Aliases: Sidecar Proxy, sidecar proxy

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Sidecar Proxy xuất hiện trong Kubernetes/service mesh khi mỗi workload có proxy chạy kèm để xử lý traffic, telemetry, mTLS, retry, timeout hoặc policy ngoài app code.

## Boundary / Ranh giới

### Nó là gì

Sidecar Proxy là proxy container/process chạy cạnh application container trong cùng pod/host boundary, intercept inbound/outbound traffic của app.

### Nó không phải là gì

Sidecar Proxy không phải business service. Nó không nên chứa domain logic; nó xử lý cross-cutting concern ở tầng traffic/runtime.

## Core Mechanism / Cơ chế lõi

Traffic của app được redirect qua sidecar. Proxy áp routing, mTLS, retries, timeout, telemetry hoặc policy rồi forward request tới service đích hoặc app local.

## Project Role / Vai trò trong dự án

Dùng node này khi debug service mesh, mTLS fail, request timeout, retry storm, traffic không tới service, telemetry thiếu hoặc overhead sidecar.

## Output / Artifact nên có

- Sidecar injection config
- Proxy route/policy config
- mTLS/cert status
- Traffic capture/log
- Resource overhead metric

## Decision Checklist / Câu hỏi kiểm tra

- Pod có sidecar injected không?
- Traffic inbound/outbound có đi qua proxy không?
- Policy nào được áp ở proxy?
- mTLS/cert có hợp lệ không?
- Sidecar có gây latency/resource overhead không?

## Failure Modes / Cách nó gây lỗi

- Sidecar injection thiếu làm policy/telemetry không áp dụng.
- Proxy config sai route làm traffic fail.
- mTLS cert lỗi gây connection refused/timeout.
- Retry ở proxy tạo retry storm.
- Sidecar resource limit thấp làm app traffic chậm.

## Khi nào chưa cần hoặc dễ over-engineer

- Service ít, traffic đơn giản có thể dùng gateway/reverse proxy trước.
- Không nên thêm service mesh/sidecar nếu team chưa cần policy/observability ở service-to-service layer.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Mesh Gateway]] vì sidecar proxy thường là phần của service mesh/gateway architecture.
- [[Reverse Proxy]] vì sidecar proxy là một dạng proxy traffic.
- [[Linkerd]] vì Linkerd dùng sidecar proxy cho service mesh.
- [[TLS]] vì mTLS/cert là chức năng phổ biến của sidecar.

## Liên quan rộng

- Service mesh
- mTLS
- Traffic policy

## Keywords / Từ khóa tìm kiếm

- Sidecar Proxy
- sidecar proxy
- service mesh sidecar
- mTLS proxy
- sidecar injection
- traffic interception
- sidecar proxy debugging

## Source trace

- Kubernetes official docs
- Linkerd documentation
- Envoy documentation
