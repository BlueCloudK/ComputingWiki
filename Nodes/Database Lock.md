# Database Lock

Aliases: DB lock, khóa cơ sở dữ liệu

Type: Database Systems

## Context / Ngữ cảnh

Database Lock xuất hiện khi database cần bảo vệ row, table, index, schema hoặc resource nội bộ trước các transaction cạnh tranh. Nó là cơ chế nền để giữ data consistency nhưng cũng là nguyên nhân phổ biến của lock wait, deadlock, timeout và latency spike.

## Boundary / Ranh giới

### Nó là gì

Database Lock là cơ chế database dùng để kiểm soát quyền đọc/ghi đồng thời. Lock có thể ở mức row, table, page, metadata hoặc advisory tùy database. Transaction giữ lock cho tới khi statement hoặc transaction kết thúc, tùy loại lock và isolation level.

### Nó không phải là gì

Database Lock không phải lỗi mặc định. Lock là cần thiết để bảo vệ dữ liệu. Vấn đề xảy ra khi lock scope quá rộng, transaction giữ lock quá lâu, thứ tự truy cập resource không nhất quán hoặc query/migration gây lock trên bảng lớn.

## Core Mechanism / Cơ chế lõi

Khi transaction đọc/ghi dữ liệu, database cấp lock hoặc dùng MVCC kết hợp lock để bảo vệ conflict. Transaction khác có thể phải chờ, bị timeout hoặc bị deadlock detector hủy nếu vòng chờ xuất hiện. Lock behavior phụ thuộc vào query plan, index, isolation level, foreign key, DDL và thời lượng transaction.

## Project Role / Vai trò trong dự án

Database Lock là node cần mở khi API chậm bất thường, transaction timeout, deadlock log xuất hiện, migration làm production đứng, hoặc một query update làm nhiều request khác chờ. Nó giúp team debug bằng lock graph, blocking query, transaction duration, index usage và thứ tự update resource.

## Output / Artifact nên có

- Lock/debug query cho database đang dùng: blocking session, waiting query, lock mode
- Transaction boundary note cho path ghi dữ liệu quan trọng
- Metric/log: lock wait time, deadlock count, transaction duration, blocked query
- Migration lock impact review cho bảng lớn hoặc DDL nguy hiểm
- Test case cho concurrent update, deadlock và retry sau serialization/deadlock failure

## Decision Checklist / Câu hỏi kiểm tra

- Transaction nào đang giữ lock lâu nhất?
- Query có dùng index đúng không, hay scan nhiều row và lock rộng hơn cần thiết?
- Có DDL/migration nào đang lock bảng production không?
- Thứ tự update nhiều table/row có nhất quán giữa các code path không?
- Isolation level hiện tại có cần lock mạnh hơn không?
- App có gọi API ngoài hoặc xử lý lâu trong transaction không?
- Deadlock/lock timeout có được retry an toàn và idempotent không?

## Failure Modes / Cách nó gây lỗi

- Transaction dài giữ lock làm request khác chờ và timeout.
- Thiếu index khiến update/delete scan nhiều row và tạo lock rộng.
- Hai transaction update resource theo thứ tự ngược nhau gây deadlock.
- Migration/DDL trên bảng lớn lock production traffic.
- Foreign key check hoặc cascade tạo lock ngoài bảng team đang nhìn.
- Retry sau lock timeout không idempotent làm duplicate side effect.

## Khi nào chưa cần hoặc dễ over-engineer

- Workload nhỏ ít concurrent write có thể chưa cần lock tuning sâu.
- Không nên thêm distributed lock nếu lock database/local transaction đã đủ bảo vệ invariant.
- Không nên tăng timeout để “né” lock wait khi nguyên nhân thật là transaction dài hoặc query thiếu index.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Transaction]] vì lock thường được giữ trong phạm vi transaction.
- [[Deadlock]] vì deadlock là failure mode trực tiếp của lock cạnh tranh.
- [[Isolation Level]] vì isolation quyết định nhiều behavior đọc/ghi và lock.
- [[Database Migration]] vì migration có thể gây lock lớn trên schema/table.
- [[Index]] vì index tốt giúp giảm số row bị scan/lock trong nhiều query.

## Liên quan rộng

- Concurrency control
- Database performance
- Incident debugging
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Database Lock
- DB lock
- khóa cơ sở dữ liệu
- row lock
- table lock
- lock wait
- deadlock
- blocking query
- lock timeout
- transaction lock
- isolation level
- MVCC
- advisory lock
- DDL lock
- database lock debugging

## Source trace

- PostgreSQL explicit locking documentation
- PostgreSQL transaction isolation documentation
