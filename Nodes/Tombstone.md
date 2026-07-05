# Tombstone

Aliases: Tombstone, delete tombstone

Type: Database Internals

## Context / Ngữ cảnh

Tombstone xuất hiện trong database/storage engine khi delete không xóa dữ liệu vật lý ngay mà ghi một marker để biểu thị record/key đã bị xóa.

## Boundary / Ranh giới

### Nó là gì

Tombstone là delete marker giúp storage engine, replication hoặc compaction biết key/row nào đã bị xóa và không nên trả về như dữ liệu sống.

### Nó không phải là gì

Tombstone không phải dữ liệu đã biến mất hoàn toàn. Nó thường còn tồn tại một thời gian trong storage/log/index để đảm bảo delete được truyền và xử lý đúng.

## Core Mechanism / Cơ chế lõi

Khi delete xảy ra, engine ghi tombstone thay vì remove ngay. Read path phải lọc tombstone. Compaction/vacuum/cleanup sau đó mới loại bỏ tombstone và data cũ khi an toàn.

## Project Role / Vai trò trong dự án

Dùng node này khi debug dữ liệu đã xóa vẫn chiếm storage, read amplification cao, compaction lag, replication delete, soft delete hoặc LSM/MVCC storage behavior.

## Output / Artifact nên có

- Tombstone count/age metric
- Delete path description
- Cleanup/compaction policy
- Read path filtering rule
- Replication/retention constraint

## Decision Checklist / Câu hỏi kiểm tra

- Tombstone được tạo khi nào?
- Cleanup an toàn sau điều kiện nào?
- Tombstone có làm read path chậm không?
- Delete đã propagate tới replica chưa?
- Retention có giữ tombstone quá lâu không?

## Failure Modes / Cách nó gây lỗi

- Tombstone tích tụ làm storage phình.
- Read path phải scan nhiều tombstone nên chậm.
- Cleanup quá sớm làm delete không propagate đủ.
- Query/debug nhầm tombstone là dữ liệu sống.
- Tombstone retention không khớp backup/replication policy.

## Khi nào chưa cần hoặc dễ over-engineer

- App dùng database managed không cần thao tác tombstone trực tiếp, chỉ cần hiểu signal bloat/cleanup.
- Không nên tự implement tombstone nếu database đã có delete/retention mechanism phù hợp.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Storage Engine]] vì tombstone là behavior của storage/write path.
- [[Read Amplification]] vì tombstone tích tụ làm đọc nhiều data thừa.
- [[Database Vacuum Lag]] vì cleanup chậm có thể giữ deleted versions lâu.
- [[Crash Recovery]] vì delete marker phải bền vững qua crash.

## Liên quan rộng

- Delete marker
- Compaction
- Soft delete

## Keywords / Từ khóa tìm kiếm

- Tombstone
- delete tombstone
- delete marker
- compaction
- deleted record
- tombstone cleanup
- tombstone debugging

## Source trace

- Designing Data-Intensive Applications
- PostgreSQL documentation
- Database System Concepts
