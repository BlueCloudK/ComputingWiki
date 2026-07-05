# Heap File

Aliases: Heap File, heap storage

Type: Database Internals

## Context / Ngữ cảnh

Heap File xuất hiện trong database storage engine khi table row được lưu không theo thứ tự index cụ thể, mà trong các page/block của vùng heap/table storage.

## Boundary / Ranh giới

### Nó là gì

Heap File là cách lưu trữ table data dưới dạng tập page chứa record/tuple, thường không đảm bảo thứ tự logic theo key.

### Nó không phải là gì

Heap File không phải heap memory của programming language runtime. Đây là khái niệm storage của database/table file.

## Core Mechanism / Cơ chế lõi

Database insert row vào page còn chỗ trống, quản lý free space và dùng row identifier/tuple pointer để index trỏ về row trong heap. Query có thể scan heap hoặc lookup heap từ index.

## Project Role / Vai trò trong dự án

Dùng node này khi hiểu table scan, index lookup, bloat, vacuum/compaction, update-heavy workload hoặc vì sao query dùng index vẫn phải đọc heap.

## Output / Artifact nên có

- Heap/table storage note
- Row/page density signal
- Index-to-heap lookup explanation
- Bloat/free space metric
- Maintenance action nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Query đang scan heap hay lookup từ index?
- Heap có bloat/free space lớn không?
- Update/delete pattern có làm table phình không?
- Index có cover đủ để tránh heap lookup không?
- Maintenance như vacuum/compact có cần không?

## Failure Modes / Cách nó gây lỗi

- Index lookup nhiều nhưng heap read vẫn đắt.
- Table bloat làm scan chậm dần.
- Row rộng làm page density thấp.
- Update/delete tạo dead tuple/free space xấu.
- Hiểu nhầm heap file là dữ liệu đã sort theo primary key.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu ít và query nhanh thì chưa cần tối ưu heap layout.
- Không nên đụng maintenance/storage khi lỗi thật nằm ở query/ORM pattern.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Storage Layout]] vì heap file là một dạng tổ chức physical storage.
- [[Index]] vì index thường trỏ về row trong heap.
- [[Query Plan]] vì plan thể hiện heap scan hoặc heap fetch.
- [[Bitmap Index Scan]] vì bitmap heap scan đọc heap page theo bitmap.

## Liên quan rộng

- Table storage
- Heap scan
- Tuple pointer
- Table bloat

## Keywords / Từ khóa tìm kiếm

- Heap File
- heap storage
- database heap
- heap scan
- table bloat
- tuple pointer
- heap file debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
