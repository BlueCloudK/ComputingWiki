# Database Migration

Aliases: schema migration, migration cơ sở dữ liệu, database schema migration

Type: Database Systems / Operations

## Context / Ngữ cảnh

Database Migration xuất hiện khi schema hoặc data của database cần thay đổi theo version cùng với code deployment. Nó đặc biệt quan trọng khi hệ thống đã có dữ liệu thật, nhiều app instances, rollback requirement hoặc zero-downtime deployment.

## Boundary / Ranh giới

### Nó là gì

Database Migration là tập thay đổi có version để biến database từ trạng thái cũ sang trạng thái mới: tạo bảng, thêm cột, đổi index, migrate dữ liệu, thay constraint hoặc backfill. Migration thường được quản lý bằng tool như Flyway/Liquibase hoặc migration system của framework.

### Nó không phải là gì

Database Migration không chỉ là “sửa DB cho chạy được”. Nó không nên là thao tác thủ công không version trong production. Migration cũng không thay thế database design; nếu schema change phá compatibility với code cũ/mới, migration vẫn có thể gây downtime hoặc data loss.

## Core Mechanism / Cơ chế lõi

Mỗi migration có thứ tự/version và được apply một lần lên database. Migration an toàn cần tính tới forward compatibility, backward compatibility, lock impact, data backfill, rollback strategy và deployment order giữa code cũ, code mới và schema mới. Thay đổi nguy hiểm thường phải chia thành nhiều bước: expand, backfill, switch read/write, cleanup.

## Project Role / Vai trò trong dự án

Database Migration ảnh hưởng trực tiếp tới release, rollback, data correctness và downtime. Khi review một thay đổi backend, team phải hỏi schema mới có tương thích với code đang chạy không, migration có lock bảng lớn không, dữ liệu cũ được backfill thế nào, và rollback sẽ làm gì nếu deploy fail.

## Output / Artifact nên có

- Migration file có version rõ ràng và được review cùng code
- Deployment plan cho schema change: expand/backfill/switch/cleanup nếu cần
- Rollback hoặc remediation note cho migration nguy hiểm
- Test migration trên dữ liệu gần giống production
- Estimate lock/time impact cho bảng lớn hoặc index mới
- Backup/restore checkpoint trước migration rủi ro cao

## Decision Checklist / Câu hỏi kiểm tra

- Code cũ có chạy được với schema mới trong thời gian rolling deploy không?
- Code mới có chạy được nếu migration chưa hoàn tất không?
- Migration có lock bảng lớn hoặc rewrite table không?
- Có backfill data không, backfill chạy online hay batch/job riêng?
- Rollback code có cần rollback schema không, và rollback schema có mất dữ liệu không?
- Migration đã chạy thử trên staging/snapshot dữ liệu đủ lớn chưa?
- Có monitoring/log để biết migration fail ở bước nào không?

## Failure Modes / Cách nó gây lỗi

- Drop/rename column trực tiếp làm code cũ đang chạy bị crash.
- Migration tạo index/alter table trên bảng lớn gây lock và downtime.
- Backfill không idempotent làm chạy lại migration sinh dữ liệu sai hoặc duplicate.
- Rollback schema làm mất dữ liệu mới sau khi code đã ghi theo format mới.
- Migration chạy khác thứ tự giữa môi trường làm staging pass nhưng production fail.
- Thiếu backup trước migration nguy hiểm khiến data corruption khó phục hồi.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype chưa có dữ liệu thật có thể reset schema đơn giản, nhưng phải chuyển sang migration khi có user/data thật.
- Không nên làm migration framework phức tạp nếu app chỉ dùng một database nhỏ và framework đã có migration tool đủ dùng.
- Không nên viết rollback tự động cho mọi migration nếu rollback đó nguy hiểm hơn remediation thủ công có kiểm soát.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Schema]] vì migration thay đổi cấu trúc schema qua thời gian.
- [[Deployment]] vì migration thường phải chạy đúng thứ tự với code release.
- [[Rollback]] vì schema rollback khác code rollback và có thể mất dữ liệu.
- [[Backup]] vì migration production rủi ro cao cần điểm phục hồi.

## Liên quan rộng

- Release engineering
- Data correctness
- Zero-downtime deployment
- Database operations

## Keywords / Từ khóa tìm kiếm

- Database Migration
- schema migration
- migration cơ sở dữ liệu
- database schema migration
- Flyway migration
- Liquibase migration
- migration rollback
- zero downtime migration
- database backfill
- alter table lock
- expand contract migration
- versioned migration
- production migration

## Source trace

- Flyway documentation
- Liquibase documentation
