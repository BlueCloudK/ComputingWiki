# WAL Segment

Aliases: WAL Segment, write-ahead log segment

Type: Database Internals

## Context / Ngữ cảnh

WAL Segment xuất hiện trong database dùng write-ahead log khi transaction log được chia thành các file/segment tuần tự để phục vụ durability, crash recovery và replication.

## Boundary / Ranh giới

### Nó là gì

WAL Segment là file/đơn vị log chứa record thay đổi đã ghi theo thứ tự trước khi data page được flush bền vững xuống storage.

### Nó không phải là gì

WAL Segment không phải backup đầy đủ của database. Nó là log thay đổi; để restore cần base backup/snapshot phù hợp và chuỗi WAL cần thiết.

## Core Mechanism / Cơ chế lõi

Transaction ghi WAL record vào segment hiện tại. Khi segment đầy, database rotate sang segment mới. WAL được dùng để redo sau crash, stream sang replica hoặc archive cho point-in-time recovery.

## Project Role / Vai trò trong dự án

Dùng node này khi debug disk đầy vì WAL, replication slot giữ WAL quá lâu, crash recovery, backup/PITR hoặc write workload tạo log quá nhanh.

## Output / Artifact nên có

- WAL generation rate
- Current segment / LSN position
- Replication slot retention
- Archive status
- Disk usage and cleanup rule

## Decision Checklist / Câu hỏi kiểm tra

- WAL tăng vì workload nào?
- Segment có được archive/cleanup không?
- Replica hoặc slot nào đang giữ WAL?
- Disk còn đủ cho worst-case lag không?
- Backup/restore có cần WAL segment này không?

## Failure Modes / Cách nó gây lỗi

- Replication slot stale giữ WAL làm disk đầy.
- Archive fail khiến PITR không đủ log.
- WAL generation spike vượt capacity disk.
- Xóa WAL thủ công làm database/restore hỏng.
- Tưởng WAL thay thế backup nên thiếu base backup.

## Khi nào chưa cần hoặc dễ over-engineer

- Managed database nhỏ có thể chỉ cần monitor storage/WAL metric cơ bản.
- Không nên chỉnh/xóa WAL thủ công nếu chưa hiểu replication và recovery chain.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Crash Recovery]] vì WAL segment dùng cho redo sau crash.
- [[Replication Stream]] vì replica nhận thay đổi từ WAL/log stream.
- [[Backup]] vì PITR cần base backup và WAL archive.
- [[Transaction]] vì WAL record gắn với transaction durability.

## Liên quan rộng

- Write-ahead log
- LSN
- PITR
- WAL archive

## Keywords / Từ khóa tìm kiếm

- WAL Segment
- write-ahead log segment
- WAL file
- LSN
- WAL archive
- replication slot
- WAL segment debugging

## Source trace

- PostgreSQL documentation
- Database System Concepts
