# Crash Recovery

Aliases: Crash Recovery, database crash recovery

Type: Database Internals

## Context / Ngữ cảnh

Crash Recovery xuất hiện khi database/process/machine dừng đột ngột nhưng hệ thống vẫn phải khôi phục dữ liệu về trạng thái nhất quán.

## Boundary / Ranh giới

### Nó là gì

Crash Recovery là cơ chế database dùng log, checkpoint, dirty page tracking và transaction state để phục hồi sau crash mà không phá vỡ durability/atomicity.

### Nó không phải là gì

Crash Recovery không phải backup restore. Recovery xử lý crash gần nhất bằng state/log hiện có; backup restore dùng bản sao dữ liệu từ thời điểm khác.

## Core Mechanism / Cơ chế lõi

Database ghi transaction log trước khi data page được flush. Sau crash, recovery đọc log/checkpoint, redo thay đổi đã commit nhưng chưa flush đủ và undo thay đổi chưa commit tùy engine.

## Project Role / Vai trò trong dự án

Dùng node này khi hiểu durability, WAL/redo log, checkpoint, database startup chậm sau crash hoặc debug data consistency sau power loss/process kill.

## Output / Artifact nên có

- Recovery log/checkpoint note
- Transaction state at crash
- Startup recovery metric
- Data consistency check
- Backup/restore boundary note

## Decision Checklist / Câu hỏi kiểm tra

- Database dùng WAL/redo log thế nào?
- Checkpoint gần nhất ở đâu?
- Transaction nào đã commit trước crash?
- Recovery mất bao lâu khi restart?
- Có test crash/restart trong staging không?

## Failure Modes / Cách nó gây lỗi

- Log flush policy yếu làm mất durability kỳ vọng.
- Recovery chạy lâu vì checkpoint quá xa.
- Disk/cache layer nói dối về fsync.
- App tưởng commit xong nhưng transaction chưa durable đúng mức.
- Không phân biệt crash recovery với backup/DR.

## Khi nào chưa cần hoặc dễ over-engineer

- App dùng managed database nhỏ có thể chưa cần biết sâu engine internals, nhưng vẫn cần hiểu durability setting.
- Không nên tự viết recovery logic nếu database đã cung cấp cơ chế chuẩn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ACID]] vì crash recovery bảo vệ atomicity/durability.
- [[Transaction]] vì recovery dựa trên transaction state.
- [[Backup]] vì backup là boundary khác với crash recovery.
- [[Incident Response]] vì crash recovery thường xảy ra trong incident.

## Liên quan rộng

- Write-ahead log
- Checkpoint
- Redo undo
- Durability

## Keywords / Từ khóa tìm kiếm

- Crash Recovery
- database crash recovery
- WAL
- redo log
- checkpoint
- durability
- crash recovery debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
- Designing Data-Intensive Applications
