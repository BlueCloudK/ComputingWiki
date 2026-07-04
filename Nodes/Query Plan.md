# Query Plan

Aliases: execution plan, kế hoạch truy vấn

Type: Database Systems

## Context / Ngữ cảnh

Query Plan xuất hiện khi cần hiểu database sẽ thực thi một query như thế nào: đọc bảng nào, dùng index nào, join ra sao, sort/hash thế nào và ước lượng số row/cost ra sao. Nó là công cụ chính để debug query chậm hoặc query chạy khác nhau giữa môi trường.

## Boundary / Ranh giới

### Nó là gì

Query Plan là kế hoạch thực thi do query optimizer chọn cho một SQL statement. Nó mô tả scan type, join order, join algorithm, filter, sort, aggregate, estimated cost, estimated rows và nếu dùng `EXPLAIN ANALYZE` thì có thêm actual time/actual rows.

### Nó không phải là gì

Query Plan không phải câu trả lời tuyệt đối cho mọi vấn đề database. Nó là góc nhìn của optimizer tại thời điểm đó, phụ thuộc vào statistics, parameter, index, data distribution và config. Plan tốt trên dev dataset nhỏ có thể rất tệ trên production data lớn.

## Core Mechanism / Cơ chế lõi

Database parser/optimizer phân tích query, ước lượng chi phí nhiều phương án dựa trên statistics và chọn plan có cost thấp. Khi chạy thật, plan có thể dùng sequential scan, index scan, nested loop, hash join, merge join, sort hoặc aggregate. Chênh lệch lớn giữa estimated rows và actual rows thường báo hiệu statistics hoặc selectivity sai.

## Project Role / Vai trò trong dự án

Query Plan là node cần mở khi API chậm do SQL, query timeout, N+1 bị nghi ngờ, index không được dùng hoặc migration/index mới không cải thiện như mong đợi. Nó giúp team quyết định thêm/sửa index, rewrite query, update statistics, đổi pagination hoặc tách query nặng khỏi request path.

## Output / Artifact nên có

- `EXPLAIN` hoặc `EXPLAIN ANALYZE` cho query quan trọng
- Notes về scan type, join algorithm, estimated rows vs actual rows
- Index decision: index nào được dùng, thiếu index nào, index nào không hiệu quả
- Benchmark trước/sau khi sửa query/index trên dữ liệu gần production
- Slow query log hoặc query performance dashboard

## Decision Checklist / Câu hỏi kiểm tra

- Query đang dùng sequential scan hay index scan, và điều đó có hợp lý với data size không?
- Estimated rows có lệch nhiều so với actual rows không?
- Join order/algorithm có làm row explosion hoặc sort/hash lớn không?
- Predicate/filter có dùng được index không, hay bị function/cast làm mất index?
- Query có sort/aggregate/pagination đắt không?
- Statistics có stale không, cần analyze/update stats không?
- Plan trên staging có đại diện production data distribution không?

## Failure Modes / Cách nó gây lỗi

- Statistics sai làm optimizer chọn plan tệ.
- Thiếu index hoặc index không phù hợp làm query scan quá nhiều row.
- Function/cast trên column làm index không được dùng.
- Join sai order hoặc thiếu predicate làm row count phình lớn.
- Query nhanh ở dev nhưng chậm production vì data distribution khác.
- Parameter sniffing/prepared statement làm plan tốt cho case này nhưng tệ cho case khác.

## Khi nào chưa cần hoặc dễ over-engineer

- Query chạy hiếm và data nhỏ có thể chưa cần tối ưu sâu.
- Không nên thêm index chỉ vì thấy sequential scan nếu table nhỏ hoặc scan rẻ hơn index.
- Không nên tối ưu query khi bottleneck thật nằm ở network, app code, lock hoặc connection pool.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Index]] vì query plan cho biết index có được dùng và có hiệu quả không.
- [[Database Query]] vì query plan là cách nhìn database thực thi query.
- [[N Plus One Query]] vì query plan/query count giúp phân biệt một query tệ và nhiều query nhỏ.
- [[Database Lock]] vì plan scan nhiều row có thể làm lock/wait nặng hơn với write query.

## Liên quan rộng

- Query optimization
- Database performance
- Slow query debugging
- Statistics

## Keywords / Từ khóa tìm kiếm

- Query Plan
- execution plan
- kế hoạch truy vấn
- EXPLAIN
- EXPLAIN ANALYZE
- query optimizer
- sequential scan
- index scan
- nested loop join
- hash join
- estimated rows
- actual rows
- query cost
- slow query
- query plan debugging

## Source trace

- PostgreSQL EXPLAIN documentation
- PostgreSQL query planner documentation
