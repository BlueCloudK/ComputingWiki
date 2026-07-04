# Kubernetes Controller

Aliases: controller Kubernetes, reconciliation controller

Type: Kubernetes

## Context / Ngữ cảnh

Kubernetes Controller xuất hiện khi cluster cần liên tục kéo actual state về desired state. Controller là lý do Kubernetes không chỉ “apply YAML một lần”, mà luôn quan sát resource và sửa lệch trạng thái theo vòng reconcile.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Controller là thành phần watch Kubernetes resources, so sánh desired state trong API server với actual state trong cluster, rồi thực hiện hành động để đưa hệ thống về trạng thái mong muốn. Deployment controller, ReplicaSet controller, Job controller và custom controller/operator đều theo mô hình này.

### Nó không phải là gì

Controller không phải scheduler, không phải kubelet và không phải manifest tĩnh. Nó cũng không tự biết business intent ngoài spec/status/resource mà nó quản lý. Nếu reconcile logic sai, controller có thể liên tục tạo/xóa/sửa resource theo cách gây sự cố.

## Core Mechanism / Cơ chế lõi

Controller chạy watch/list resource, nhận event hoặc requeue, rồi reconcile từng object. Reconcile loop đọc spec, kiểm tra actual state, tạo/sửa/xóa resource con, cập nhật status và dùng owner reference/finalizer khi cần. Controller phải xử lý idempotent vì cùng một reconcile có thể chạy nhiều lần.

## Project Role / Vai trò trong dự án

Kubernetes Controller giúp team hiểu vì sao resource trong cluster tự sinh lại sau khi bị xóa, vì sao rollout tiếp tục chạy, hoặc vì sao custom operator không đưa hệ thống về trạng thái mong muốn. Khi debug Kubernetes, cần biết controller nào đang owning resource và reconcile đang fail ở bước nào.

## Output / Artifact nên có

- Desired-state model: resource nào là source of truth, resource nào là child/generated
- Controller ownership map: ownerReferences, labels, finalizers
- Reconcile flow hoặc runbook cho controller/custom operator
- Metric/log: reconcile count, reconcile error, queue depth, requeue rate
- Test case cho idempotent reconcile, delete/finalizer và partial failure

## Decision Checklist / Câu hỏi kiểm tra

- Controller đang watch resource nào và own resource nào?
- Reconcile có idempotent không nếu chạy nhiều lần?
- Status có phản ánh trạng thái thật hay chỉ ghi trạng thái mong muốn?
- OwnerReference/finalizer có thể làm resource không xóa được không?
- Controller có đủ RBAC để đọc/ghi resource cần thiết không?
- Khi reconcile fail, có retry/backoff/log rõ không?
- Có tránh reconcile loop vô hạn do chính controller update resource liên tục không?

## Failure Modes / Cách nó gây lỗi

- Reconcile logic sai làm controller liên tục tạo/xóa/sửa resource.
- Finalizer không được clear làm resource stuck ở trạng thái terminating.
- RBAC thiếu quyền khiến controller thấy event nhưng không sửa được resource.
- Status update quá thường xuyên tạo event loop và tăng tải API server.
- OwnerReference/label sai làm controller nhận nhầm resource hoặc garbage collect nhầm.
- Controller crash hoặc queue backlog làm desired state không được áp dụng kịp.

## Khi nào chưa cần hoặc dễ over-engineer

- App chỉ cần Deployment/Service/ConfigMap cơ bản không cần custom controller riêng.
- Không nên viết operator nếu Helm/Kustomize/job đơn giản đã đủ cho lifecycle.
- Custom controller chỉ đáng làm khi có domain state cần reconcile lâu dài, không phải chỉ để chạy script deploy.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes]] vì controller là cơ chế lõi giúp Kubernetes duy trì desired state.
- [[Kubernetes RBAC]] vì controller cần quyền đọc/ghi resource trong reconcile loop.
- [[Kubernetes Service]] vì Service/EndpointSlice cũng được controller liên quan duy trì.
- [[Deployment]] vì Deployment controller quản lý ReplicaSet và rollout.

## Liên quan rộng

- Operator pattern
- Control loop
- Cluster operations
- Desired state management

## Keywords / Từ khóa tìm kiếm

- Kubernetes Controller
- controller Kubernetes
- reconciliation controller
- reconcile loop
- desired state
- actual state
- Kubernetes operator
- ownerReference
- finalizer
- controller runtime
- reconcile error
- controller queue
- status update
- custom controller

## Source trace

- Kubernetes controllers documentation
- controller-runtime documentation
