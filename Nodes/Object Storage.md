# Object Storage

Aliases: object store, lưu trữ object, blob storage, cloud object storage, lưu trữ đối tượng

Type: Data / Database

## Context / Ngữ cảnh

Object Storage xuất hiện khi cần lưu file/blob lớn, static asset, backup, export, log archive, data lake object hoặc file upload của user. Nó thường dùng qua bucket/container và API như S3-compatible object storage, không dùng như filesystem local hay relational database.

## Boundary / Ranh giới

### Nó là gì

Object Storage lưu dữ liệu dạng object: key, content bytes, metadata, version nếu bật và access policy. Nó tối ưu cho put/get/list object, durability cao, lifecycle/retention policy, encryption, signed URL và integration với CDN/data pipeline/backup.

### Nó không phải là gì

Object Storage không phải filesystem POSIX đầy đủ và không phải database transaction. Nó không phù hợp cho update nhỏ liên tục trong file, lock file kiểu local FS, query theo field phức tạp hoặc transaction nhiều object. Nếu cần constraint/transaction/query rich, database hoặc filesystem riêng có thể phù hợp hơn.

## Core Mechanism / Cơ chế lõi

Client gọi API để put/get/list/delete object theo bucket và key. Access được kiểm soát bằng IAM/bucket policy/ACL/signed URL. Lifecycle rule có thể chuyển storage class hoặc xóa sau thời gian. Versioning, encryption, object lock và retention giúp durability/compliance nhưng cần cấu hình đúng.

## Project Role / Vai trò trong dự án

Object Storage là node cần mở khi thiết kế upload/download, static asset hosting, backup, data lake, report export hoặc attachment system. Nó giúp team quyết định bucket/key naming, public/private boundary, signed URL, lifecycle cost, retention và cách tránh public leak.

## Output / Artifact nên có

- Bucket/container inventory: owner, purpose, environment, data class
- Key naming convention và partition prefix nếu object nhiều
- Access policy: private/public, signed URL, IAM role, service account
- Lifecycle/retention/encryption/versioning decision
- Monitoring: object count, storage cost, public access finding, failed put/get, delete events
- Backup/restore hoặc export/import runbook nếu object là dữ liệu quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Object này public, private hay chỉ accessible qua signed URL?
- Object có chứa PII, secret, user upload hoặc dữ liệu regulated không?
- Bucket policy có wildcard/public access ngoài ý muốn không?
- Key naming có tránh collision, traversal-like confusion và tenant leak không?
- Lifecycle/retention có phù hợp cost và compliance không?
- Có cần versioning/object lock để chống xóa nhầm/ransomware không?
- CDN/cache có làm stale hoặc public hóa object không?

## Failure Modes / Cách nó gây lỗi

- Bucket/object public ngoài ý muốn làm lộ file riêng tư.
- Signed URL TTL quá dài hoặc leak trong log/referrer.
- Lifecycle thiếu làm storage cost phình lớn.
- Lifecycle quá mạnh xóa backup/export trước khi cần restore.
- Dùng object storage như database transactional làm consistency/debug phức tạp.
- Key chứa tenant/user/path không kiểm soát dẫn tới overwrite hoặc cross-tenant leak.
- Không bật versioning/backup cho object quan trọng nên xóa nhầm không khôi phục được.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu nhỏ, cần query/transaction chặt có thể để trong database trước.
- Không nên tạo data lake/blob layer nếu chưa có object lifecycle và consumer thật.
- Không nên public bucket để “cho tiện” nếu signed URL/proxy access phù hợp hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Lake]] vì data lake thường lưu raw/curated object trên object storage.
- [[Backup]] vì backup thường được lưu ở object storage tách biệt.
- [[File Upload Security]] vì user-uploaded file thường nằm trong object storage.
- [[CDN]] vì static asset/object public thường được phục vụ qua CDN.
- [[Least Privilege]] vì bucket/IAM policy cần quyền tối thiểu để tránh leak hoặc delete rộng.

## Liên quan rộng

- Blob storage
- Static assets
- Cloud storage
- Data retention

## Keywords / Từ khóa tìm kiếm

- Object Storage
- object store
- blob storage
- cloud object storage
- lưu trữ đối tượng
- bucket
- object key
- S3
- signed URL
- bucket policy
- object lifecycle
- versioning
- object lock
- public bucket
- object storage debugging

## Source trace

- AWS Well-Architected Framework
- Cloud object storage documentation
