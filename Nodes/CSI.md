# CSI

Aliases: CSI, Container Storage Interface

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

CSI xuất hiện trong Kubernetes khi workload cần mount persistent storage từ cloud disk, network storage hoặc storage system bên ngoài cluster.

## Boundary / Ranh giới

### Nó là gì

CSI là chuẩn/plugin interface cho container orchestration gọi storage provider để provision, attach, mount, resize và snapshot volume.

### Nó không phải là gì

CSI không phải PersistentVolume tự thân. PV/PVC là resource Kubernetes; CSI driver là phần thực thi tích hợp storage backend.

## Core Mechanism / Cơ chế lõi

Kubernetes control plane và node plugin gọi CSI driver để tạo volume, attach vào node, mount vào pod và xử lý lifecycle. StorageClass quyết định driver, parameter và reclaim policy.

## Project Role / Vai trò trong dự án

Dùng node này khi debug PVC pending, pod mount fail, volume attach timeout, storage performance, snapshot/resize hoặc data persistence trong Kubernetes.

## Output / Artifact nên có

- CSI driver name/version
- StorageClass config
- PV/PVC mapping
- Reclaim/resize/snapshot policy
- Node attach/mount debug checklist

## Decision Checklist / Câu hỏi kiểm tra

- PVC dùng StorageClass nào?
- CSI driver có chạy trên control plane/node đúng không?
- Volume attach được vào node chưa?
- Access mode có khớp workload không?
- Reclaim policy có phù hợp dữ liệu production không?

## Failure Modes / Cách nó gây lỗi

- PVC pending vì StorageClass/driver sai.
- Pod mount fail do node plugin lỗi.
- Volume bị xóa vì reclaim policy không phù hợp.
- Access mode sai làm nhiều pod không mount được.
- Resize/snapshot tưởng hỗ trợ nhưng driver không bật.

## Khi nào chưa cần hoặc dễ over-engineer

- Stateless workload không cần CSI/PersistentVolume.
- Không nên dùng storage động cho dữ liệu quan trọng nếu backup/restore chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Persistent Volume]] vì CSI thường provision/mount PV cho pod.
- [[Kubernetes Service]] vì stateful app sau service vẫn cần storage ổn định.
- [[Managed Kubernetes]] vì provider thường cung cấp CSI driver riêng.
- [[Cloud Backup Policy]] vì persistent volume production cần backup/restore policy.

## Liên quan rộng

- Kubernetes storage
- Persistent volume
- StorageClass

## Keywords / Từ khóa tìm kiếm

- CSI
- Container Storage Interface
- Kubernetes CSI
- CSI driver
- StorageClass
- PVC pending
- volume mount
- CSI debugging

## Source trace

- Kubernetes official docs
- Container Storage Interface specification
