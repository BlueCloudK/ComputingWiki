# Linkerd

Aliases: Linkerd

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Linkerd xuất hiện khi Kubernetes service cần service mesh nhẹ để thêm mTLS, telemetry, traffic policy và reliability behavior giữa service-to-service mà không sửa app code quá nhiều.

## Boundary / Ranh giới

### Nó là gì

Linkerd là service mesh cho Kubernetes, dùng control plane và sidecar proxy để quản lý traffic giữa workload.

### Nó không phải là gì

Linkerd không phải API gateway public và không thay thế toàn bộ observability stack. Nó tập trung vào service-to-service traffic bên trong cluster.

## Core Mechanism / Cơ chế lõi

Workload được inject sidecar proxy. Traffic inbound/outbound đi qua proxy; control plane cấp identity/cert, thu telemetry và áp policy/route theo config.

## Project Role / Vai trò trong dự án

Dùng node này khi debug mTLS, service mesh latency, traffic policy, retry/timeout, telemetry giữa service hoặc quyết định có cần mesh trong Kubernetes không.

## Output / Artifact nên có

- Mesh install/version note
- Namespace/workload injection status
- mTLS identity/cert status
- Traffic policy/route config
- Linkerd dashboard/metrics check

## Decision Checklist / Câu hỏi kiểm tra

- Workload có được inject proxy chưa?
- Traffic có đi qua sidecar không?
- mTLS có bật và cert hợp lệ không?
- Policy/route nào áp lên request này?
- Mesh overhead có đáng so với lợi ích không?

## Failure Modes / Cách nó gây lỗi

- Namespace chưa inject nên telemetry/policy thiếu.
- mTLS identity/cert lỗi làm request fail.
- Proxy resource limit thấp làm tăng latency.
- Mesh policy block traffic nhưng app log không rõ.
- Thêm mesh khi team chưa có nhu cầu/khả năng vận hành.

## Khi nào chưa cần hoặc dễ over-engineer

- Hệ thống ít service có thể dùng ingress/reverse proxy và monitoring đơn giản trước.
- Không nên thêm service mesh chỉ vì “production-looking” nếu chưa có pain về mTLS, traffic policy hoặc service observability.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Sidecar Proxy]] vì Linkerd dùng sidecar proxy cho data plane.
- [[Kubernetes Controller]] vì control plane vận hành theo controller/reconciliation.
- [[TLS]] vì mTLS là chức năng lõi của Linkerd.
- [[Monitoring]] vì Linkerd cung cấp telemetry service-to-service.

## Liên quan rộng

- Service mesh
- mTLS
- Traffic policy

## Keywords / Từ khóa tìm kiếm

- Linkerd
- service mesh
- Linkerd sidecar
- Linkerd mTLS
- Linkerd dashboard
- Linkerd policy
- Linkerd debugging

## Source trace

- Linkerd documentation
- Kubernetes official docs
