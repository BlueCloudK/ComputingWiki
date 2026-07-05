# Index

Aliases: database index, chỉ mục database

Type: Data / Database

## Context / Ngữ cảnh

Index xuất hiện khi database cần tìm, lọc, join, sort hoặc enforce uniqueness nhanh hơn so với quét toàn bộ bảng. Nó là một trong các công cụ chính để tối ưu query path trong backend production, đặc biệt khi dữ liệu tăng từ vài nghìn lên vài triệu row.

## Boundary / Ranh giới

### Nó là gì

Index là cấu trúc dữ liệu phụ được database duy trì để truy cập row theo column/expression nhanh hơn. Index phổ biến là B-tree, ngoài ra có hash, GIN/GiST, full-text, spatial hoặc columnar tùy database. Index cũng có thể là unique index để enforce constraint.

### Nó không phải là gì

Index không tự làm mọi query nhanh. Nếu query filter/sort không khớp index, statistics sai, selectivity thấp hoặc query phải đọc quá nhiều row, index có thể không được dùng hoặc còn chậm hơn. Index cũng không miễn phí: nó tốn storage và làm write/migration chậm hơn vì database phải cập nhật index.

## Core Mechanism / Cơ chế lõi

Khi có index phù hợp, query planner có thể dùng index scan để tìm row theo key/range/order thay vì sequential scan. Composite index phụ thuộc thứ tự column. Covering index có thể giảm lookup về table. Partial/expression index chỉ hiệu quả khi query predicate khớp điều kiện index.

## Project Role / Vai trò trong dự án

Index là node cần mở khi API chậm do SQL, query plan scan nhiều row, sort đắt, join chậm, unique rule cần enforce hoặc migration thêm index gây lock/downtime. Nó giúp team quyết định index nào cần tạo, đo trước/sau và tránh thêm index theo cảm tính.

## Output / Artifact nên có

- Query pattern cần tối ưu: filter, join, sort, pagination, uniqueness
- `EXPLAIN` / `EXPLAIN ANALYZE` trước và sau khi thêm index
- Index definition: columns, order, unique/partial/expression/covering nếu có
- Migration plan: online/concurrent index, lock impact, rollback/drop plan
- Monitoring: slow query, index usage, write latency, index size

## Decision Checklist / Câu hỏi kiểm tra

- Query nào thật sự chậm và có query plan chứng minh không?
- Predicate/sort/join có khớp column order của index không?
- Selectivity có đủ cao để index hữu ích không?
- Composite index có dùng đúng leftmost prefix không?
- Index mới có làm write/migration/storage tăng đáng kể không?
- Có thể dùng unique index để enforce invariant thay vì chỉ validate ở app không?
- Index có được tạo online/concurrently nếu bảng lớn không?

## Failure Modes / Cách nó gây lỗi

- Thêm index không khớp query nên database vẫn sequential scan.
- Quá nhiều index làm insert/update/delete chậm và storage phình lớn.
- Migration tạo index trên bảng lớn gây lock hoặc downtime.
- Composite index sai thứ tự column nên query chính không dùng được.
- Function/cast trên column làm index thường không được dùng.
- Unique rule chỉ kiểm tra ở app, thiếu unique index, gây duplicate dưới concurrency.
- Index tốt ở dev nhưng không hiệu quả production vì data distribution khác.

## Khi nào chưa cần hoặc dễ over-engineer

- Bảng nhỏ hoặc query hiếm chạy có thể chưa cần index mới.
- Không nên thêm index chỉ vì “có vẻ cần” nếu chưa có slow query/query plan.
- Không nên tối ưu index khi bottleneck thật là lock, connection pool, network hoặc N+1 query.

## Gồm những gì

- [[Benchmark]]

## Nối mạnh

- [[Query Plan]] vì query plan cho biết index có được dùng và có hiệu quả không.
- [[Database Migration]] vì thêm/sửa index thường đi qua migration và có lock impact.
- [[N Plus One Query]] vì thiếu index có thể làm N+1 tệ hơn, nhưng query count vẫn cần xử lý riêng.
- [[Database Lock]] vì index creation/write path có thể liên quan lock/wait.
- [[Validation]] vì unique index/constraint bảo vệ invariant tốt hơn chỉ validate ở app.

## Liên quan rộng

- Database performance
- Query optimization
- Data modeling
- Production migration

## Keywords / Từ khóa tìm kiếm

- Index
- database index
- chỉ mục database
- B-tree index
- composite index
- covering index
- partial index
- expression index
- unique index
- index scan
- sequential scan
- index selectivity
- leftmost prefix
- concurrent index
- index debugging

## Source trace

- Database System Concepts
- PostgreSQL indexes documentation
