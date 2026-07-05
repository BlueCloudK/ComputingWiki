# Limit Range

Aliases: Limit Range, Kubernetes LimitRange

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Limit Range xuất hiện trong Kubernetes namespace khi cluster cần đặt default/min/max CPU, memory hoặc storage request/limit cho pod/container/PVC.

## Boundary / Ranh giới

### Nó là gì

Limit Range là Kubernetes object dùng để áp rule resource request/limit trong phạm vi namespace.

### Nó không phải là gì

Limit Range không phải ResourceQuota. Limit Range đặt default/min/max cho từng object; ResourceQuota giới hạn tổng tài nguyên cả namespace.

## Core Mechanism / Cơ chế lõi

Admission controller kiểm tra object mới trong namespace. Nếu container thiếu request/limit, LimitRange có thể inject default. Nếu request/limit vượt min/max, object bị reject.

## Project Role / Vai trò trong dự án

Dùng node này khi debug pod bị reject, pod pending do request quá lớn, workload không có resource limit, node pool bị overcommit hoặc namespace cần policy mặc định.

## Output / Artifact nên có

- LimitRange manifest
- Default request/limit
- Min/max per resource
- Namespace scope
- Failure example từ admission event

## Decision Checklist / Câu hỏi kiểm tra

- Namespace nào áp LimitRange này?
- Default request/limit có hợp workload không?
- Min/max có làm pod hợp lệ bị reject không?
- ResourceQuota có xung đột với default request không?
- Limit có gây throttling hoặc OOM không?

## Failure Modes / Cách nó gây lỗi

- Default request quá cao làm pod pending vì thiếu capacity.
- Default limit quá thấp làm app bị OOM/throttle.
- Min/max chặn workload hợp lệ nhưng lỗi nhìn như deploy fail.
- LimitRange và ResourceQuota cộng lại làm namespace hết quota nhanh.
- Không có LimitRange khiến container thiếu request/limit và scheduling khó đoán.

## Khi nào chưa cần hoặc dễ over-engineer

- Cluster nhỏ/lab có thể bắt đầu bằng request/limit trực tiếp trong manifest.
- Không nên đặt default quá chặt nếu chưa hiểu memory/CPU profile của workload.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Resource Quota]] vì LimitRange và ResourceQuota thường đi cùng ở namespace policy.
- [[Node Pool]] vì request/limit ảnh hưởng scheduling lên node pool.
- [[Kubernetes Controller]] vì workload controller tạo pod bị admission policy kiểm tra.
- [[Resource Exhaustion]] vì limit/request sai có thể gây OOM/throttling hoặc thiếu capacity.

## Liên quan rộng

- Kubernetes admission
- Resource request
- CPU memory limit

## Keywords / Từ khóa tìm kiếm

- Limit Range
- Kubernetes LimitRange
- resource request
- resource limit
- default limit
- pod admission
- LimitRange debugging

## Source trace

- Kubernetes official docs
