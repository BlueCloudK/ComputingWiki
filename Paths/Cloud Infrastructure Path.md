# Cloud Infrastructure Path

## Mục tiêu

Path này giúp người đọc hiểu hạ tầng cloud/container từ network, compute, storage tới Kubernetes và operation.

## Khi nào dùng path này

- Khi deploy app lên cloud hoặc Kubernetes.
- Khi debug network, load balancer, pod, storage hoặc permission.
- Khi thiết kế infrastructure cho service production.

## 1. Cloud building blocks

- [[Cloud Computing]] — mô hình dùng compute/storage/network qua provider.
- [[Region]] — vùng địa lý cloud chạy workload.
- [[Availability Zone]] — failure domain trong region.
- [[VPC]] — network riêng trong cloud.
- [[IAM]] — identity và permission cho cloud resource.
- [[Object Storage]] — storage object cho file/blob.

## 2. Traffic và network

- [[DNS]] — map name sang address.
- [[Load Balancer]] — phân phối traffic tới backend.
- [[TLS]] — bảo vệ connection.
- [[HTTPS]] — HTTP chạy qua TLS.
- [[Nginx]] — web server/reverse proxy phổ biến.
- [[Reverse Proxy]] — proxy đứng trước service thật.
- [[CDN]] — cache/phân phối content gần user.

## 3. Container foundation

- [[Docker]] — build/run container.
- [[Docker Compose]] — chạy nhiều container local hoặc nhỏ.
- [[Container Image]] — artifact để chạy container.
- [[Container Registry]] — nơi lưu image.
- [[Container Runtime]] — runtime chạy container trên node.

## 4. Kubernetes foundation

- [[Kubernetes]] — orchestration platform cho container workload.
- [[Kubernetes Cluster]] — cụm control plane và nodes.
- [[Kubernetes Node]] — machine chạy pod.
- [[Kubernetes Pod]] — đơn vị scheduling nhỏ nhất.
- [[Kubernetes Deployment]] — controller rollout stateless workload.
- [[Kubernetes Service]] — stable network endpoint cho pod.
- [[Kubernetes Ingress]] — expose HTTP(S) vào cluster.

## 5. Kubernetes operation

- [[ConfigMap]] — config không nhạy cho workload.
- [[Kubernetes Secret]] — secret trong Kubernetes.
- [[Kubernetes RBAC]] — permission trong cluster.
- [[Service Account]] — identity cho workload.
- [[Kubernetes Probe]] — health signal cho container.
- [[Persistent Volume]] — storage bền cho workload.
- [[Network Policy]] — kiểm soát traffic pod.
- [[Horizontal Pod Autoscaler]] — scale pod theo metric.

## 6. Infrastructure as code

- [[Infrastructure as Code]] — quản lý hạ tầng bằng file.
- [[Terraform]] — tool IaC phổ biến.
- [[Helm]] — package/template cho Kubernetes.
- [[Kustomize]] — overlay manifest Kubernetes.
- [[Deployment Strategy]] — rollout an toàn.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Subnet
- Security group
- Cloud billing
- Managed database
- GitOps
- Observability stack

## Related paths

- [[DevOps Deployment Path]]
- [[Security Engineering Path]]
- [[Debugging and Failure Patterns Path]]
- [[Backend Engineering Path]]
