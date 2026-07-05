# Flux CD

Aliases: Flux CD, Flux

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Flux CD xuất hiện khi Kubernetes cluster cần GitOps controller tự đồng bộ trạng thái từ Git/registry vào cluster.

## Boundary / Ranh giới

### Nó là gì

Flux CD là bộ controller GitOps cho Kubernetes, theo dõi source như Git repository hoặc OCI artifact, rồi reconcile manifest/Kustomize/Helm release vào cluster.

### Nó không phải là gì

Flux CD không phải CI build tool. Nó không build/test code chính; nó kéo desired state đã được publish và làm cluster tiến về state đó.

## Core Mechanism / Cơ chế lõi

Flux source controller fetch source, kustomize/helm controller render/apply resource, image automation có thể cập nhật version, và reconciliation loop liên tục so sánh desired state với cluster state.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế GitOps deploy, debug Kubernetes drift, Helm release fail, image update automation hoặc production rollout từ Git.

## Output / Artifact nên có

- Git/OCI source config
- Kustomization hoặc HelmRelease
- Reconciliation interval
- Image policy/update rule nếu có
- Alert/log/debug checklist

## Decision Checklist / Câu hỏi kiểm tra

- Source of truth nằm ở repo/path nào?
- Controller nào đang reconcile resource này?
- Drift có bị Flux sửa lại không?
- Secret/credential lấy từ đâu?
- Rollback bằng revert Git hay thao tác cluster trực tiếp?

## Failure Modes / Cách nó gây lỗi

- Sửa tay trong cluster bị Flux revert mà không hiểu vì sao.
- Git path/source sai nên controller không thấy manifest.
- Helm/Kustomize render fail làm deploy đứng.
- Credential thiếu làm source fetch fail.
- Image automation update nhầm tag hoặc quá nhanh.

## Khi nào chưa cần hoặc dễ over-engineer

- Cluster nhỏ deploy thủ công hoặc CI apply đơn giản có thể chưa cần GitOps controller.
- Không nên thêm Flux nếu team chưa thống nhất Git là source of truth.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CD]] vì Flux là cơ chế continuous delivery theo GitOps.
- [[Kubernetes Controller]] vì Flux vận hành bằng controller reconciliation.
- [[Git Remote]] vì Git repository thường là source of truth.
- [[Rollback]] vì rollback GitOps thường là revert commit/version.

## Liên quan rộng

- GitOps
- Kubernetes reconciliation
- Helm release

## Keywords / Từ khóa tìm kiếm

- Flux CD
- Flux
- GitOps
- Kustomization
- HelmRelease
- reconciliation
- Flux debugging

## Source trace

- Flux documentation
- Kubernetes official docs
