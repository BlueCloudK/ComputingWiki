# Storage Engine

Aliases: Storage Engine, database storage engine

Type: Database Internals

## Context / Ngữ cảnh

Storage Engine xuất hiện khi cần hiểu database thật sự lưu, đọc, ghi, index, cache, log và khôi phục dữ liệu như thế nào dưới lớp SQL/API.

## Boundary / Ranh giới

### Nó là gì

Storage Engine là thành phần chịu trách nhiệm quản lý physical data layout, page/cache, index, write path, transaction log, compaction/vacuum và crash recovery.

### Nó không phải là gì

Storage Engine không phải query language hay ORM. SQL/ORM là lớp biểu đạt thao tác; storage engine là lớp thực thi dữ liệu ở mức lưu trữ.

## Core Mechanism / Cơ chế lõi

Engine nhận operation từ executor/transaction layer, đọc/ghi page hoặc segment, cập nhật index/log, giữ consistency theo transaction rule và tối ưu I/O bằng cache/layout/compaction.

## Project Role / Vai trò trong dự án

Dùng node này khi debug database chậm, I/O cao, bloat, lock, crash recovery, replication lag hoặc khi chọn database phù hợp workload.

## Output / Artifact nên có

- Storage layout note
- Read/write path diagram
- Index/cache/log behavior
- Performance metric: I/O, cache hit, latency
- Failure/recovery behavior

## Decision Checklist / Câu hỏi kiểm tra

- Workload chủ yếu read, write hay mixed?
- Engine dùng row-store, LSM, heap hay kiểu khác?
- Write path có log/checkpoint/compaction gì?
- Read path có index/cache/filter gì?
- Failure recovery và durability được đảm bảo ra sao?

## Failure Modes / Cách nó gây lỗi

- Chọn database theo API mà không hiểu storage tradeoff.
- Write amplification hoặc read amplification tăng theo scale.
- Cache/layout không hợp workload làm I/O cao.
- Compaction/vacuum tụt làm latency và disk tăng.
- Recovery/replication behavior không khớp kỳ vọng production.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ dùng managed database có thể chưa cần đào sâu toàn bộ internals.
- Không nên tối ưu storage engine khi bottleneck thật nằm ở query/app/network.

## Gồm những gì

- [[Storage Layout]]
- [[Page Cache]]
- [[Crash Recovery]]
- [[Read Amplification]]

## Nối mạnh

- [[Storage Layout]] vì layout là phần lõi của storage engine.
- [[Page Cache]] vì cache page ảnh hưởng read path.
- [[Crash Recovery]] vì engine phải khôi phục sau crash.
- [[Index]] vì index là access path do engine quản lý.

## Liên quan rộng

- Database internals
- Write path
- Read path
- Durability

## Keywords / Từ khóa tìm kiếm

- Storage Engine
- database storage engine
- read path
- write path
- storage layout
- transaction log
- storage engine debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
- Designing Data-Intensive Applications
