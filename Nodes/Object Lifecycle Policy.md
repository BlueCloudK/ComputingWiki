# Object Lifecycle Policy

Aliases: Object Lifecycle Policy, object storage lifecycle

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Object Lifecycle Policy xuất hiện khi object storage chứa log, backup, artifact, upload hoặc archive và cần tự động chuyển tier, expire hoặc delete theo thời gian.

## Boundary / Ranh giới

### Nó là gì

Object Lifecycle Policy là rule trên bucket/object storage để quản lý vòng đời object: transition storage class, expire version cũ, delete incomplete upload hoặc retention theo prefix/tag.

### Nó không phải là gì

Object Lifecycle Policy không phải backup policy đầy đủ. Nó chỉ quản lý object đã có; backup strategy còn cần RPO/RTO, restore test, encryption và access control.

## Core Mechanism / Cơ chế lõi

Policy match object bằng prefix/tag/version/age, rồi object storage tự thực hiện action như move sang cold/archive tier, delete noncurrent version hoặc abort multipart upload.

## Project Role / Vai trò trong dự án

Dùng node này khi kiểm soát chi phí storage, giữ log/backup đúng retention, dọn artifact cũ hoặc debug vì sao object bị xóa/chuyển tier ngoài ý muốn.

## Output / Artifact nên có

- Lifecycle rule list
- Prefix/tag scope
- Retention duration
- Transition/delete action
- Restore/cost impact note

## Decision Checklist / Câu hỏi kiểm tra

- Object loại nào được policy match?
- Retention cần giữ bao lâu?
- Có versioning/noncurrent version không?
- Chuyển sang cold tier có ảnh hưởng restore time không?
- Delete rule có đụng dữ liệu cần giữ pháp lý/audit không?

## Failure Modes / Cách nó gây lỗi

- Prefix quá rộng xóa nhầm object quan trọng.
- Chuyển sang archive làm restore chậm khi incident.
- Không xử lý version cũ nên cost vẫn tăng.
- Lifecycle policy xung đột retention/legal hold.
- Không test restore nên tưởng object còn dùng được ngay.

## Khi nào chưa cần hoặc dễ over-engineer

- Bucket nhỏ, dữ liệu ít và chưa có cost/retention concern có thể chưa cần policy phức tạp.
- Không nên thêm delete rule nếu chưa có owner và retention requirement rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Object Storage]] vì lifecycle policy áp trên object storage.
- [[Backup]] vì backup object cần retention và restore rule rõ.
- [[Cloud Budget Alert]] vì lifecycle policy giúp kiểm soát storage cost.
- [[Release Artifact]] vì artifact cũ thường cần retention/delete policy.

## Liên quan rộng

- Storage retention
- Cold storage
- Log retention

## Keywords / Từ khóa tìm kiếm

- Object Lifecycle Policy
- object storage lifecycle
- lifecycle rule
- retention policy
- storage class transition
- object expiration
- lifecycle policy debugging

## Source trace

- AWS S3 documentation
- Google Cloud Storage documentation
- Azure Blob Storage documentation
