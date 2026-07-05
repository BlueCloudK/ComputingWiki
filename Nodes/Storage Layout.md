# Storage Layout

Aliases: Storage Layout, physical storage layout

Type: Database Internals

## Context / Ngữ cảnh

Storage Layout xuất hiện khi cần hiểu database lưu row, page, index, heap/table file và metadata trên disk/memory như thế nào.

## Boundary / Ranh giới

### Nó là gì

Storage Layout là cách database tổ chức dữ liệu vật lý: page/block, row format, heap/table file, index structure, free space, visibility metadata và đôi khi partition/shard layout.

### Nó không phải là gì

Storage Layout không phải schema logic. Schema nói table/column/constraint; storage layout nói dữ liệu thật được đặt và đọc/ghi ra sao.

## Core Mechanism / Cơ chế lõi

Storage engine chia dữ liệu thành page/block, đặt row/tuple vào page, dùng metadata để quản lý free space/visibility và dùng index hoặc scan để tìm row. Layout ảnh hưởng I/O, cache locality, bloat và query plan.

## Project Role / Vai trò trong dự án

Dùng node này khi debug query chậm, table bloat, I/O cao, index behavior, vacuum/compaction hoặc storage growth bất thường.

## Output / Artifact nên có

- Table/page layout note
- Row size/bloat estimate
- Index/storage mapping
- Query plan with I/O signal
- Maintenance plan: vacuum/compact/reindex nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu được đọc theo page/block nào?
- Row size có làm page density thấp không?
- Bloat/free space có cao không?
- Query đang scan heap hay dùng index?
- Maintenance có ảnh hưởng lock/latency không?

## Failure Modes / Cách nó gây lỗi

- Schema logic tốt nhưng physical layout gây I/O lớn.
- Row quá rộng làm cache/page efficiency thấp.
- Table/index bloat làm query chậm dần.
- Update pattern tạo dead tuple/free space xấu.
- Không hiểu layout nên tối ưu sai ở layer ORM/app.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ với data ít có thể chưa cần đào sâu storage layout.
- Không nên tối ưu layout khi bottleneck thật nằm ở query pattern hoặc network.

## Gồm những gì

- [[Heap File]]

## Nối mạnh

- [[Query Plan]] vì planner chọn cách đọc dữ liệu dựa trên storage/index/statistics.
- [[Index]] vì index là một phần quan trọng của physical access path.
- [[Bitmap Index Scan]] vì bitmap scan cho thấy cách index/page được đọc.
- [[Performance Optimization]] vì layout ảnh hưởng I/O và cache locality.

## Liên quan rộng

- Page layout
- Storage engine
- Table bloat
- Disk I/O

## Keywords / Từ khóa tìm kiếm

- Storage Layout
- physical storage layout
- database page
- row format
- heap storage
- table bloat
- storage engine
- storage layout debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
- Designing Data-Intensive Applications
