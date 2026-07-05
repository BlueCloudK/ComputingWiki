# Cloud Backup Policy

Aliases: Cloud Backup Policy, backup policy

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Cloud Backup Policy xuất hiện khi dữ liệu, config hoặc artifact quan trọng cần được sao lưu định kỳ để phục hồi sau lỗi người dùng, lỗi hệ thống, ransomware, corruption hoặc region failure.

## Boundary / Ranh giới

### Nó là gì

Cloud Backup Policy là rule xác định cái gì được backup, tần suất, retention, encryption, access control, restore test và owner chịu trách nhiệm.

### Nó không phải là gì

Backup policy không phải chỉ bật snapshot. Nếu không test restore, backup có thể tồn tại nhưng không dùng được khi incident thật.

## Core Mechanism / Cơ chế lõi

Policy chọn resource, tạo schedule backup/snapshot/export, lưu bản backup ở storage/region phù hợp, mã hóa và kiểm soát quyền, rồi định kỳ test restore và audit retention.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế disaster recovery, database backup, object storage versioning, infrastructure backup hoặc compliance retention.

## Output / Artifact nên có

- Backup scope
- Schedule và retention
- Encryption/access rule
- Restore test checklist
- RPO/RTO target
- Owner/on-call note

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu nào bắt buộc backup?
- RPO/RTO là bao nhiêu?
- Backup nằm cùng region hay cross-region?
- Ai có quyền xóa/restore backup?
- Restore test đã chạy gần đây chưa?

## Failure Modes / Cách nó gây lỗi

- Backup có nhưng restore fail.
- Retention quá ngắn làm mất điểm phục hồi cần thiết.
- Backup nằm cùng failure domain với dữ liệu gốc.
- Quyền xóa backup quá rộng.
- Không backup config/secret cần thiết để khôi phục app.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu disposable có thể không cần backup formal.
- Không nên mua backup/DR phức tạp khi RPO/RTO chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Backup]] vì cloud backup policy cụ thể hóa backup trong môi trường cloud.
- [[Incident Response]] vì restore thường xảy ra trong incident.
- [[Object Storage]] vì backup thường nằm trong object storage/versioning.
- [[Least Privilege]] vì quyền đọc/xóa backup phải hạn chế.

## Liên quan rộng

- Disaster recovery
- Data retention
- Cloud storage

## Keywords / Từ khóa tìm kiếm

- Cloud Backup Policy
- backup policy
- backup retention
- restore test
- RPO RTO
- cross-region backup
- cloud backup debugging

## Source trace

- Google SRE Books
- AWS Backup documentation
