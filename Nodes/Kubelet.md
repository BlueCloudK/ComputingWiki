# Kubelet

Aliases: Kubernetes node agent, kubelet

Type: Kubernetes

## Context / Ngữ cảnh

Kubelet xuất hiện trên mỗi Kubernetes node để nhận Pod spec từ control plane, phối hợp với container runtime chạy container, gắn volume, kiểm tra health probe và báo trạng thái node/pod về API server. Nó là cầu nối giữa desired state của cluster và workload thật trên node.

## Boundary / Ranh giới

### Nó là gì

Kubelet là node agent của Kubernetes. Nó watch Pod được assign cho node, tạo/sync container qua Container Runtime Interface, quản lý probe, volume mount, cgroup/resource, pod status và node status. Nếu kubelet hỏng hoặc mất liên lạc, node có thể thành NotReady và Pod status không còn cập nhật đúng.

### Nó không phải là gì

Kubelet không phải scheduler, không quyết định Pod chạy ở node nào. Nó cũng không phải container runtime như containerd; kubelet gọi runtime để tạo/chạy container. Kubelet không thay thế controller; controller quyết định desired state, kubelet thực thi phần được giao trên node.

## Core Mechanism / Cơ chế lõi

Kubelet chạy pod sync loop: nhận Pod spec, đảm bảo sandbox/container/volume/network tương ứng tồn tại, chạy liveness/readiness/startup probe, thu thập status và gửi heartbeat/node condition về API server. Nó phối hợp với container runtime, CNI plugin, CSI/volume plugin và host OS.

## Project Role / Vai trò trong dự án

Kubelet là node cần kiểm tra khi Pod stuck ContainerCreating, volume mount fail, probe fail, image pull lỗi, node NotReady hoặc container restart bất thường. Khi debug Kubernetes sâu hơn service/deployment, kubelet log và node status giúp biết lỗi nằm ở node agent, runtime, network, volume hay app container.

## Output / Artifact nên có

- Node health checklist: node status, kubelet service status, kubelet logs, runtime status
- Pod debug path: describe pod, events, kubelet logs, container runtime logs
- Probe configuration review: liveness, readiness, startup probe
- Resource/runtime note: CPU/memory pressure, disk pressure, image pull, volume mount
- Runbook cho NodeNotReady, ContainerCreating, CrashLoopBackOff và probe failure

## Decision Checklist / Câu hỏi kiểm tra

- Node có Ready không, kubelet có gửi heartbeat đều không?
- Pod bị lỗi ở scheduling, image pull, volume mount, container start hay probe?
- Kubelet log có báo lỗi runtime/CNI/CSI không?
- Readiness/liveness/startup probe có đúng path/port/timeout không?
- Node có MemoryPressure/DiskPressure/PIDPressure không?
- Container runtime như containerd có healthy không?
- Volume hoặc secret/config mount có đúng namespace/quyền/path không?

## Failure Modes / Cách nó gây lỗi

- Kubelet mất kết nối API server làm node NotReady và status không cập nhật.
- Container runtime lỗi khiến Pod không start dù spec đúng.
- CNI/network setup fail làm Pod stuck ContainerCreating.
- Volume mount hoặc secret/config mount fail làm container không chạy được.
- Probe cấu hình sai làm kubelet kill/restart container liên tục.
- Node disk/memory pressure làm eviction hoặc image pull thất bại.

## Khi nào chưa cần hoặc dễ over-engineer

- Khi mới học Kubernetes ở mức app, thường chỉ cần hiểu Pod/Service/Deployment trước.
- Không nên debug kubelet trước khi đã kiểm tra `kubectl describe pod`, events và manifest cơ bản.
- Managed Kubernetes che bớt kubelet config, nhưng kubelet behavior vẫn cần hiểu khi debug node/pod issue.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes]] vì kubelet là node agent cốt lõi của Kubernetes.
- [[Pod]] vì kubelet thực thi Pod spec trên node được assign.
- [[Container Runtime]] vì kubelet gọi runtime để chạy container.
- [[Health Check]] vì kubelet thực thi liveness/readiness/startup probes.
- [[Persistent Volume]] vì kubelet tham gia mount volume vào Pod trên node.

## Liên quan rộng

- Node operations
- Cluster debugging
- Container runtime
- Kubernetes events

## Keywords / Từ khóa tìm kiếm

- Kubelet
- Kubernetes node agent
- kubelet debugging
- node NotReady
- pod sync loop
- container runtime interface
- liveness probe
- readiness probe
- startup probe
- volume mount fail
- ContainerCreating
- CrashLoopBackOff
- Node pressure
- kubelet logs
- Kubernetes node status

## Source trace

- Kubernetes kubelet documentation
- Kubernetes node documentation
