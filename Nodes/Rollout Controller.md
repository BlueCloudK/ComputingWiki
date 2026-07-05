# Rollout Controller

Aliases: Rollout Controller, rollout controller

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Rollout Controller xuất hiện khi deployment cần được điều phối theo từng bước như canary, blue-green, progressive delivery hoặc tự rollback khi metric xấu.

## Boundary / Ranh giới

### Nó là gì

Rollout Controller là controller/operator quản lý rollout state, traffic shifting, analysis gate, pause/resume và rollback cho một workload hoặc release.

### Nó không phải là gì

Rollout Controller không thay thế test, monitoring hoặc deployment approval. Nó chỉ tự động hóa rollout decision dựa trên config và signal được cung cấp.

## Core Mechanism / Cơ chế lõi

Controller quan sát desired rollout spec và current cluster/runtime state, tạo ReplicaSet/service/traffic policy tương ứng, tăng traffic theo step, chạy analysis và quyết định continue, pause hoặc rollback.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế progressive delivery, canary release, automated rollback, traffic split hoặc debug rollout stuck/paused/failed.

## Output / Artifact nên có

- Rollout spec
- Traffic step plan
- Analysis template/metric
- Pause/rollback rule
- Status/debug command checklist

## Decision Checklist / Câu hỏi kiểm tra

- Rollout strategy là canary, blue-green hay step rollout?
- Metric nào quyết định pass/fail?
- Traffic tăng theo bước nào?
- Rollback tự động hay cần approval?
- Controller status nói đang kẹt ở step nào?

## Failure Modes / Cách nó gây lỗi

- Metric thiếu hoặc sai làm rollout pass mù.
- Traffic router/service selector sai làm canary không nhận đúng traffic.
- Rollout pause nhưng không ai nhận trách nhiệm resume/rollback.
- Controller và CD pipeline tranh quyền apply resource.
- Rollback nhanh nhưng migration/data change không rollback được.

## Khi nào chưa cần hoặc dễ over-engineer

- Service nhỏ ít traffic có thể dùng deployment strategy đơn giản trước.
- Không nên dùng rollout controller nếu monitoring metric chưa đáng tin.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Progressive Delivery]] vì rollout controller thực thi progressive rollout.
- [[Canary Analysis]] vì analysis gate quyết định rollout tiếp hay dừng.
- [[Rollback]] vì controller có thể rollback khi fail.
- [[Kubernetes Controller]] vì rollout controller thường là Kubernetes controller/operator.

## Liên quan rộng

- Canary rollout
- Traffic shifting
- Automated rollback

## Keywords / Từ khóa tìm kiếm

- Rollout Controller
- rollout controller
- progressive rollout
- canary controller
- analysis gate
- traffic shifting
- rollout controller debugging

## Source trace

- Kubernetes official docs
- Argo Rollouts documentation
- Continuous Delivery
