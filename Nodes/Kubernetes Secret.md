# Kubernetes Secret

Aliases: K8s Secret, secret Kubernetes

Type: Kubernetes / Security

## Context / Ngữ cảnh

Kubernetes Secret xuất hiện khi Pod cần dùng dữ liệu nhạy cảm như password, token, API key, TLS certificate hoặc registry credential. Nó giúp tách secret khỏi image/source code/ConfigMap, nhưng vẫn cần RBAC, encryption và secret rotation đúng.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Secret là resource lưu data nhạy cảm để Pod consume qua environment variable hoặc mounted volume. Secret data thường được encode base64 trong manifest/API object; base64 không phải encryption. Secret an toàn phụ thuộc vào RBAC, etcd encryption, access policy và external secret workflow nếu có.

### Nó không phải là gì

Kubernetes Secret không tự là secret manager hoàn chỉnh. Nếu commit manifest secret vào Git, cấp RBAC quá rộng hoặc không bật encryption at rest, secret vẫn có thể lộ. Nó cũng không tự rotate secret hoặc reload app khi secret thay đổi nếu workload không được thiết kế cho việc đó.

## Core Mechanism / Cơ chế lõi

Secret được tạo trong namespace, kubelet mount vào Pod qua volume hoặc inject thành env var. Pod/service account cần quyền phù hợp để dùng secret. Update secret không luôn làm app reload ngay; env var thường cần Pod restart, còn mounted volume có thể cập nhật file nhưng app phải đọc lại.

## Project Role / Vai trò trong dự án

Kubernetes Secret là node cần mở khi deploy app cần database password/API token/cert, debug Pod thiếu credential, rotate secret, review RBAC hoặc tách config nhạy cảm khỏi ConfigMap. Nó giúp team hiểu secret đi từ source of truth tới runtime Pod bằng đường nào.

## Output / Artifact nên có

- Secret inventory: name, namespace, owner, purpose, consuming workload
- Delivery method: env var, mounted file, imagePullSecret hoặc external secret
- RBAC/access policy: ai/service account nào được read/list/watch secret
- Rotation plan: trigger, rollout/restart, validation, rollback
- Security note: encryption at rest, Git handling, audit log, external secret manager nếu dùng

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu này có thật sự là secret không, hay chỉ là config thường?
- Secret có bị commit plaintext/base64 vào repo không?
- ServiceAccount/RBAC nào có quyền đọc secret này?
- Secret được inject qua env var hay mounted file, và app reload thế nào khi rotate?
- Namespace boundary có đúng tenant/app không?
- Etcd/encryption at rest/audit log có phù hợp môi trường không?
- Có external secret manager hoặc sealed/encrypted manifest nếu cần GitOps không?

## Failure Modes / Cách nó gây lỗi

- Base64 bị hiểu nhầm là encryption và secret bị commit vào Git.
- RBAC quá rộng cho phép nhiều Pod/user đọc secret không cần thiết.
- Secret rotate nhưng Pod không restart/reload nên app vẫn dùng credential cũ.
- Inject secret qua env var rồi bị log/crash dump lộ ra.
- Secret nằm sai namespace hoặc thiếu key làm Pod crash/missing config.
- Dùng ConfigMap cho password/token vì tiện, làm lộ dữ liệu nhạy cảm.

## Khi nào chưa cần hoặc dễ over-engineer

- Local dev có thể dùng `.env` hoặc secret local đơn giản, nhưng không nên mang thói quen đó lên production.
- Không nên dùng Kubernetes Secret cho mọi config không nhạy cảm; ConfigMap phù hợp hơn.
- Không nên tự chế secret rotation nếu provider/external secret manager đã hỗ trợ tốt hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Secret]] vì Kubernetes Secret là cách Kubernetes đóng gói secret cho workload.
- [[ConfigMap]] vì cần phân biệt config thường và secret nhạy cảm.
- [[Kubernetes RBAC]] vì quyền đọc secret phải được giới hạn rất chặt.
- [[Environment Variable]] vì secret có thể được inject vào Pod qua env var.
- [[Deployment]] vì rotate/update secret thường cần rollout hoặc restart workload.

## Liên quan rộng

- Application security
- Platform engineering
- Secret rotation
- GitOps

## Keywords / Từ khóa tìm kiếm

- Kubernetes Secret
- K8s Secret
- secret Kubernetes
- Secret volume
- secret env var
- imagePullSecret
- base64 secret
- etcd encryption
- RBAC secret access
- secret rotation
- external secrets
- sealed secrets
- Kubernetes secret debugging

## Source trace

- Kubernetes Secrets documentation
- Kubernetes RBAC documentation
