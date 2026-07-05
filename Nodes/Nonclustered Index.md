# Nonclustered Index

Aliases: Nonclustered Index, secondary index

Type: Database Internals

## Context / Ngữ cảnh

Nonclustered Index xuất hiện khi database cần tăng tốc truy vấn theo một hoặc nhiều cột mà không thay đổi thứ tự lưu trữ chính của bảng.

## Boundary / Ranh giới

### Nó là gì

Nonclustered Index là index riêng biệt trỏ từ key index tới row/table data. Nó còn hay được hiểu như secondary index trong nhiều hệ database.

### Nó không phải là gì

Nonclustered Index không phải miễn phí. Nó tăng tốc read pattern nhất định nhưng làm write/update/delete tốn thêm chi phí và cần storage.

## Core Mechanism / Cơ chế lõi

Database lưu cấu trúc index theo key. Query planner có thể dùng index để tìm row nhanh hơn, sau đó lookup dữ liệu còn lại từ table nếu index không cover đủ column.

## Project Role / Vai trò trong dự án

Dùng node này khi debug query chậm, thiết kế index cho filter/sort/join, xem query plan hoặc cân bằng read performance với write overhead.

## Output / Artifact nên có

- Index definition
- Target query pattern
- Query plan before/after
- Write overhead note
- Covering column decision nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Query nào cần index này?
- Predicate/sort/join column có đúng thứ tự không?
- Index có cover đủ column không?
- Write overhead có chấp nhận được không?
- Index có trùng với index khác không?

## Failure Modes / Cách nó gây lỗi

- Thêm index nhưng planner không dùng vì selectivity thấp.
- Quá nhiều index làm write chậm.
- Index thiếu column nên lookup vẫn đắt.
- Index trùng lặp gây storage và maintenance cost.
- Thống kê cũ làm planner chọn plan sai.

## Khi nào chưa cần hoặc dễ over-engineer

- Bảng nhỏ hoặc query hiếm chạy chưa cần thêm index.
- Không nên thêm index chỉ vì thấy query chậm một lần mà chưa xem plan/metric.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Index]] vì nonclustered index là một dạng index.
- [[Query Plan]] vì planner quyết định có dùng index hay không.
- [[N Plus One Query]] vì index không sửa được pattern gọi query quá nhiều lần.
- [[Write Amplification]] vì nhiều index làm mỗi write tốn thêm công.

## Liên quan rộng

- Secondary index
- Query optimization
- Storage overhead

## Keywords / Từ khóa tìm kiếm

- Nonclustered Index
- secondary index
- covering index
- index lookup
- query plan
- nonclustered index debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
