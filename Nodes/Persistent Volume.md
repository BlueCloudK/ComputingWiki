# Persistent Volume

Aliases: PV, Kubernetes persistent volume

Type: Kubernetes / Storage

## Context / Ngữ cảnh

Persistent Volume xuất hiện khi Pod cần storage bền vững không mất theo vòng đời container hoặc Pod. Nó thường dùng cho database, file upload, message broker state, model/data cache, hoặc app cần đọc/ghi dữ liệu nằm ngoài container image.

## Boundary / Ranh giới

### Nó là gì

Persistent Volume là resource đại diện cho storage trong Kubernetes cluster. Pod thường không dùng PV trực tiếp mà dùng PersistentVolumeClaim để yêu cầu storage theo size, access mode và StorageClass. PV có lifecycle tách khỏi Pod nên dữ liệu có thể tồn tại sau khi Pod bị xóa hoặc reschedule.

### Nó không phải là gì

Persistent Volume không tự đảm bảo backup, replication, encryption hoặc performance. Nó cũng không thay thế database replication hay object storage. Nếu dùng sai access mode, reclaim policy hoặc storage class, dữ liệu có thể không mount được, bị mất sau delete hoặc bị kẹt ở trạng thái không bind.

## Core Mechanism / Cơ chế lõi

Admin hoặc dynamic provisioner tạo PV dựa trên StorageClass. User tạo PVC để claim storage. Kubernetes bind PVC với PV phù hợp, kubelet mount volume vào Pod trên node. Reclaim policy như Retain/Delete quyết định volume thật được giữ hay xóa khi claim bị xóa. Access mode quyết định volume có thể mount read/write bởi bao nhiêu node.

## Project Role / Vai trò trong dự án

Persistent Volume là node cần mở khi workload stateful chạy trên Kubernetes, Pod restart mất dữ liệu, PVC Pending, volume mount fail, hoặc app cần backup/restore. Nó giúp team phân biệt dữ liệu nằm trong container layer, emptyDir, PV/PVC, object storage hay database managed bên ngoài.

## Output / Artifact nên có

- PV/PVC manifest hoặc Helm values: size, access mode, StorageClass, reclaim policy
- Data ownership note: dữ liệu gì nằm trên volume, ai backup/restore
- Backup/restore runbook cho workload stateful
- Mount path và permission/fsGroup decision
- Monitoring: volume usage, mount error, provision error, IOPS/latency nếu storage hỗ trợ

## Decision Checklist / Câu hỏi kiểm tra

- Workload này thật sự cần storage bền vững hay chỉ cần emptyDir/cache tạm?
- PVC yêu cầu access mode nào: ReadWriteOnce, ReadOnlyMany hay ReadWriteMany?
- StorageClass có hỗ trợ dynamic provisioning và performance cần thiết không?
- Reclaim policy là Retain hay Delete, và khi xóa PVC dữ liệu sẽ ra sao?
- Pod có mount đúng path, quyền user/group và filesystem không?
- Có backup/restore test cho dữ liệu trên volume không?
- Nếu Pod reschedule sang node khác, volume có attach/mount được không?

## Failure Modes / Cách nó gây lỗi

- PVC Pending vì không có StorageClass/PV phù hợp.
- Pod stuck ContainerCreating do volume attach/mount fail.
- Reclaim policy Delete làm mất dữ liệu khi PVC bị xóa nhầm.
- ReadWriteOnce volume không mount được nhiều node như workload mong đợi.
- Permission sai làm app không ghi được vào mount path.
- Không monitor dung lượng khiến volume đầy và database/app fail.
- Không backup volume nên node/storage failure thành mất dữ liệu thật.

## Khi nào chưa cần hoặc dễ over-engineer

- Stateless app không cần ghi dữ liệu bền vững thì không cần PV.
- Cache có thể rebuild được có thể dùng emptyDir hoặc external cache thay vì PV phức tạp.
- Database production quan trọng đôi khi nên dùng managed database ngoài cluster thay vì tự vận hành PV nếu team chưa đủ ops maturity.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes]] vì Persistent Volume là storage abstraction của Kubernetes.
- [[Kubelet]] vì kubelet mount volume vào Pod trên node.
- [[Pod]] vì Pod dùng PVC để mount storage.
- [[Backup]] vì dữ liệu trên PV cần backup/restore strategy riêng.
- [[StatefulSet]] vì workload stateful thường dùng PVC ổn định theo Pod identity.

## Liên quan rộng

- Kubernetes storage
- Stateful workload
- Disaster recovery
- StorageClass

## Keywords / Từ khóa tìm kiếm

- Persistent Volume
- PV
- Kubernetes persistent volume
- PersistentVolumeClaim
- PVC
- StorageClass
- reclaim policy
- ReadWriteOnce
- ReadWriteMany
- volume binding
- volume mount fail
- PVC Pending
- Kubernetes storage
- stateful workload
- persistent volume debugging

## Source trace

- Kubernetes Persistent Volumes documentation
