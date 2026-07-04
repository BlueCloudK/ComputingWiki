# Helm

Aliases: Helm chart, Kubernetes package manager, Helm Kubernetes

Type: Cloud / Kubernetes

## Context / Ngữ cảnh

Helm xuất hiện khi Kubernetes manifest cần được đóng gói, template hóa, version và deploy lặp lại qua nhiều môi trường. Nó thường dùng để triển khai app, dependency như database/cache, hoặc platform component vào cluster.

## Boundary / Ranh giới

### Nó là gì

Helm là package manager/template system cho Kubernetes. Một chart chứa template manifest, `values.yaml`, metadata và helper template. Khi install/upgrade, Helm render template thành Kubernetes resources và quản lý chúng như một release có revision, history và rollback.

### Nó không phải là gì

Helm không thay thế hiểu biết về Kubernetes manifest thật. Template render ra YAML sai thì cluster vẫn fail như thường. Helm cũng không tự giải quyết secret management, drift, policy, rollout safety hoặc environment design; nó chỉ là lớp đóng gói và render/deploy.

## Core Mechanism / Cơ chế lõi

Helm lấy chart + values, render template thành manifest, rồi apply vào cluster theo release. `values.yaml` quyết định khác biệt giữa môi trường. Upgrade tạo revision mới, rollback quay về revision cũ nhưng không phải lúc nào cũng hoàn tác được external state như database migration, PVC hoặc side effect ngoài cluster.

## Project Role / Vai trò trong dự án

Helm ảnh hưởng tới cách team chuẩn hóa deployment Kubernetes, chia config theo môi trường, reuse chart và rollback release. Khi vận hành cluster, Helm giúp biết tài nguyên nào thuộc release nào, chart version nào đang chạy và values nào tạo ra manifest hiện tại.

## Output / Artifact nên có

- Helm chart structure: Chart.yaml, values.yaml, templates, helpers
- Values file theo môi trường: dev/staging/prod
- Rendered manifest check bằng `helm template` hoặc CI lint
- Release upgrade/rollback runbook
- Chart versioning và app versioning convention
- Policy cho secret/config: cái gì nằm trong values, cái gì nằm ở secret manager

## Decision Checklist / Câu hỏi kiểm tra

- Chart có render ra manifest đúng với values của từng môi trường không?
- `values.yaml` có đang chứa secret hoặc config nhạy cảm không?
- Upgrade có thay đổi immutable field hoặc resource name không?
- Rollback Helm có đủ an toàn nếu release kèm database migration/PVC không?
- Chart version và app image tag có được pin rõ không?
- CI có chạy `helm lint` và render manifest trước khi deploy không?
- Values override có quá rối làm khó biết production đang chạy cấu hình nào không?

## Failure Modes / Cách nó gây lỗi

- Template sai indentation/type làm manifest render được nhưng apply fail.
- Values môi trường sai làm service trỏ nhầm image, port, secret hoặc resource limit.
- Rollback Helm không rollback được data/schema/external state, gây mismatch với app version.
- Chart quá generic làm values phình to và khó review.
- Dùng latest image tag hoặc không pin chart version làm deploy không reproducible.
- Drift giữa tài nguyên chỉnh tay bằng kubectl và release Helm làm upgrade sau đó khó đoán.

## Khi nào chưa cần hoặc dễ over-engineer

- App rất nhỏ một vài manifest có thể dùng YAML thuần hoặc Kustomize trước.
- Không nên viết chart quá generic cho mọi app nếu chỉ có một app cụ thể.
- Không nên dùng Helm để che việc team chưa hiểu Kubernetes resources được render ra.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes]] vì Helm deploy và quản lý Kubernetes resources.
- [[Deployment]] vì Helm thường là công cụ release app lên cluster.
- [[Rollback]] vì Helm quản lý release history và rollback revision.
- [[ConfigMap]] vì values thường render ra ConfigMap hoặc cấu hình app.

## Liên quan rộng

- GitOps
- Platform engineering
- Release management
- Environment configuration

## Keywords / Từ khóa tìm kiếm

- Helm
- Helm chart
- Kubernetes package manager
- Helm Kubernetes
- values.yaml
- helm template
- helm install
- helm upgrade
- helm rollback
- chart version
- release revision
- Kubernetes templating
- helm lint
- rendered manifest
- helm debugging

## Source trace

- Helm documentation
