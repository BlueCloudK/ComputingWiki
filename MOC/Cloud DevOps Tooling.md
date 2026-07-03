# Cloud DevOps Tooling

Aliases: cloud tooling, DevOps tooling, platform tooling, công cụ cloud DevOps

Type: MOC

## Context / Ngữ cảnh

Cloud DevOps Tooling là vùng kiến thức về IaC, CI/CD, GitOps, observability, artifact, runtime platform và vận hành cloud.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC điều hướng cho các node thuộc Cloud / DevOps Tooling.

### Nó không phải là gì

Nó không phải tutorial dài hoặc danh sách tool rời rạc; mục tiêu là map khái niệm để đi tiếp trong graph.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom node theo boundary, workflow, artifact, failure mode và operational signal.

## Project Role / Vai trò trong dự án

MOC này giúp chọn node cần đọc khi thiết kế, debug, deploy hoặc audit một phần hệ thống.

## Output / Artifact nên có

- Pack map
- Navigation links
- Source trace cấp vùng

## Decision Checklist / Câu hỏi kiểm tra

- Node mới có thuộc pack này thật không?
- Node đó có source trace và boundary rõ không?
- Link có giúp navigation hay chỉ làm graph nhiễu?

## Failure Modes / Cách nó gây lỗi

- Pack quá rộng làm người đọc không biết đi đâu
- Link quá nhiều làm graph nhiễu
- Node quá tool-specific nhưng không có cơ chế ổn định phía sau

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần chia sâu hơn nếu node chưa được dùng trong path hoặc project workflow
- Dễ over-engineer nếu biến MOC thành course hoặc tutorial

## Gồm những gì

- [[GitOps]]
- [[Infrastructure Drift]]
- [[Terraform State]]
- [[Terraform Plan]]
- [[Terraform Apply]]
- [[Terraform Module]]
- [[Terraform Provider]]
- [[Terraform Workspace]]
- [[Remote State]]
- [[State Locking]]
- [[Cloud Resource Tagging]]
- [[Cloud Cost Management]]
- [[Cloud Budget Alert]]
- [[Cloud Quota]]
- [[Cloud Limit]]
- [[Cloud Policy]]
- [[Security Group]]
- [[Network ACL]]
- [[Private Subnet]]
- [[Public Subnet]]
- [[NAT Gateway]]
- [[Bastion Host]]
- [[Jump Server]]
- [[Managed Database]]
- [[Managed Kubernetes]]
- [[Serverless Function]]
- [[Cloud Run]]
- [[Object Lifecycle Policy]]
- [[Cloud Backup Policy]]
- [[Cloud Secret Manager]]
- [[GitHub Actions]]
- [[Pipeline Runner]]
- [[Self Hosted Runner]]
- [[Build Cache]]
- [[Artifact Repository]]
- [[Artifact Signing]]
- [[Release Artifact]]
- [[Deployment Approval]]
- [[Environment Promotion]]
- [[Pipeline Secret]]
- [[Pipeline Variable]]
- [[Matrix Build]]
- [[Workflow Dispatch]]
- [[Deployment Gate]]
- [[Quality Gate]]
- [[Policy as Code]]
- [[OPA]]
- [[Conftest]]
- [[Checkov]]
- [[Trivy]]
- [[Helm Chart]]
- [[Helm Release]]
- [[Helm Values]]
- [[Ingress Controller]]
- [[Cert Manager]]
- [[External DNS]]
- [[Cluster Autoscaler]]
- [[Node Pool]]
- [[Pod Security Standard]]
- [[Resource Quota]]
- [[Limit Range]]
- [[Kubernetes Context]]
- [[Kubectl]]
- [[Kubeconfig]]
- [[Container Runtime Interface]]
- [[CNI]]
- [[CSI]]
- [[Service Mesh]]
- [[Sidecar Proxy]]
- [[Envoy]]
- [[Istio]]
- [[Linkerd]]
- [[API Mesh Gateway]]
- [[Traffic Mirroring]]
- [[Progressive Delivery]]
- [[Canary Analysis]]
- [[Blue Green Switch]]
- [[Rollout Controller]]
- [[Argo CD]]
- [[Flux CD]]
- [[OpenTelemetry]]
- [[Telemetry Collector]]
- [[Metric Backend]]
- [[Log Aggregation]]
- [[Trace Sampling]]
- [[Span]]
- [[Dashboard]]
- [[Service Dashboard]]
- [[Alert Rule]]
- [[Alert Routing]]
- [[On Call Rotation]]
- [[Runbook Automation]]
- [[ChatOps]]
- [[Incident Channel]]
- [[Status Page]]
- [[Maintenance Window]]
- [[Change Freeze]]
- [[Feature Freeze]]
- [[Capacity Review]]
- [[Cost Review]]

## Nối mạnh


- Chưa có nối mạnh ngoài các node con trực tiếp
## Liên quan rộng

- Cloud and Infrastructure
- Deployment and Operations
- Linux and Server Admin
- SRE and Reliability
- ComputingWiki expansion pack
- Project-oriented knowledge graph

## Keywords / Từ khóa tìm kiếm

- Cloud DevOps Tooling
- cloud tooling
- DevOps tooling
- platform tooling
- công cụ cloud DevOps

## Source trace

- Kubernetes official docs
- OpenTelemetry documentation
- Terraform documentation
- GitHub Actions documentation
