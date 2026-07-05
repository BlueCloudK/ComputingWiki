# Cert Manager

Aliases: Cert Manager, cert-manager

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Cert Manager xuất hiện trong Kubernetes khi cluster cần tự động cấp, gia hạn và quản lý TLS certificate cho Ingress, Gateway hoặc service.

## Boundary / Ranh giới

### Nó là gì

Cert Manager là Kubernetes controller/operator quản lý certificate lifecycle thông qua custom resources như Certificate, Issuer và ClusterIssuer.

### Nó không phải là gì

Cert Manager không phải TLS termination proxy. Nó cấp và lưu certificate; việc terminate TLS thường do Ingress, Gateway, load balancer hoặc app thực hiện.

## Core Mechanism / Cơ chế lõi

User khai báo Certificate trỏ tới Issuer/ClusterIssuer. Cert Manager tạo request tới CA như ACME/Let’s Encrypt hoặc internal CA, hoàn thành challenge nếu cần, rồi ghi certificate/key vào Kubernetes Secret và tự renew trước khi hết hạn.

## Project Role / Vai trò trong dự án

Dùng node này khi debug HTTPS lỗi, certificate hết hạn, ACME challenge fail, Ingress không có TLS secret hoặc tự động hóa certificate trong Kubernetes.

## Output / Artifact nên có

- Certificate manifest
- Issuer/ClusterIssuer config
- TLS Secret name
- Renewal status
- Challenge/order/event logs

## Decision Checklist / Câu hỏi kiểm tra

- Certificate dùng Issuer nào?
- DNS/HTTP challenge có route đúng không?
- TLS Secret có được tạo và mount đúng không?
- Certificate sắp hết hạn có renew được không?
- Ingress/Gateway có trỏ đúng secret không?

## Failure Modes / Cách nó gây lỗi

- ACME challenge fail vì DNS/Ingress route sai.
- Issuer secret/credential thiếu làm cấp cert fail.
- Certificate renew không kịp gây HTTPS outage.
- Ingress dùng sai TLS secret.
- Rate limit Let’s Encrypt vì tạo/xóa cert nhiều lần.

## Khi nào chưa cần hoặc dễ over-engineer

- Lab local có thể dùng self-signed/manual cert trước.
- Không nên tự động cấp public cert nếu DNS và ownership domain chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[TLS]] vì cert-manager quản lý certificate dùng cho TLS.
- [[Kubernetes Secret]] vì certificate/key thường được lưu trong Secret.
- [[Ingress Controller]] vì Ingress thường dùng cert từ cert-manager.
- [[Kubernetes Controller]] vì cert-manager vận hành bằng reconciliation loop.

## Liên quan rộng

- Certificate lifecycle
- ACME challenge
- HTTPS automation

## Keywords / Từ khóa tìm kiếm

- Cert Manager
- cert-manager
- Kubernetes certificate
- ACME challenge
- ClusterIssuer
- TLS Secret
- cert-manager debugging

## Source trace

- cert-manager documentation
- Kubernetes official docs
