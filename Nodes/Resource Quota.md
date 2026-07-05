# Resource Quota

Aliases: Resource Quota, Kubernetes ResourceQuota

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Resource Quota xuất hiện trong Kubernetes namespace khi cluster cần giới hạn tổng CPU, memory, storage, object count hoặc số workload mà một team/app được phép dùng.

## Boundary / Ranh giới

### Nó là gì

Resource Quota là Kubernetes object đặt quota tổng theo namespace cho resource request/limit, PVC, pod, service, configmap hoặc object type khác.

### Nó không phải là gì

Resource Quota không đặt default request/limit cho từng container. Việc đó là vai trò của LimitRange; quota chỉ chặn tổng usage vượt ngưỡng.

## Core Mechanism / Cơ chế lõi

Admission controller tính usage hiện tại trong namespace. Khi object mới được tạo/cập nhật, nếu vượt hard quota, request bị reject. Nếu object thiếu request/limit cần thiết cho quota, nó cũng có thể bị chặn.

## Project Role / Vai trò trong dự án

Dùng node này khi debug deploy bị reject do quota, chia tài nguyên giữa team, ngăn namespace ăn hết cluster, hoặc thiết kế capacity policy cho Kubernetes.

## Output / Artifact nên có

- ResourceQuota manifest
- Hard quota values
- Current used values
- Namespace owner
- Exception/escalation rule

## Decision Checklist / Câu hỏi kiểm tra

- Namespace này được phép dùng tối đa bao nhiêu CPU/memory/storage?
- Workload có request/limit rõ để tính quota không?
- Quota có khớp capacity node pool không?
- Khi quota đầy, owner xử lý scale/downsize hay xin tăng?
- LimitRange có giúp default request/limit không?

## Failure Modes / Cách nó gây lỗi

- Deploy fail vì quota đầy nhưng lỗi bị hiểu nhầm là CI/CD fail.
- Quota quá thấp làm team không chạy được workload hợp lệ.
- Quota quá cao khiến một namespace chiếm cluster.
- Không có request/limit nên object bị reject khi quota yêu cầu.
- Quota và autoscaling không khớp làm scale-out bị chặn.

## Khi nào chưa cần hoặc dễ over-engineer

- Cluster lab một người có thể chưa cần quota formal.
- Không nên đặt quota nếu chưa có owner/capacity policy rõ, vì dễ tạo lỗi vận hành khó hiểu.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Limit Range]] vì LimitRange hỗ trợ default/min/max để quota hoạt động ổn hơn.
- [[Node Pool]] vì quota phải khớp capacity thực tế của node pool.
- [[Resource Exhaustion]] vì quota giúp ngăn một namespace làm cạn tài nguyên cluster.
- [[Kubernetes Controller]] vì controller tạo pod/object có thể bị admission quota chặn.

## Liên quan rộng

- Namespace policy
- Kubernetes admission
- Cluster capacity

## Keywords / Từ khóa tìm kiếm

- Resource Quota
- Kubernetes ResourceQuota
- namespace quota
- CPU memory quota
- hard quota
- quota exceeded
- resource quota debugging

## Source trace

- Kubernetes official docs
