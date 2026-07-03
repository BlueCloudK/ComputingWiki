# N Plus One Query

Aliases: N Plus One Query, N+1 Query, N+1 query, truy vấn N cộng 1

Type: Failure Pattern / Database

## Context / Ngữ cảnh

N Plus One Query xuất hiện khi code lấy một danh sách record bằng 1 query, rồi tiếp tục gọi thêm 1 query cho từng record để lấy relation/child data. Nó thường xảy ra trong ORM, template rendering, API list endpoint, GraphQL resolver hoặc loop xử lý dữ liệu.

## Boundary / Ranh giới

### Nó là gì

N Plus One Query là failure pattern trong đó số query tăng theo số lượng item thay vì giữ gần như hằng số hoặc tăng theo batch. Ví dụ lấy 100 orders rồi query customer cho từng order sẽ thành 1 + 100 queries thay vì join/eager load/batch query.

### Nó không phải là gì

N Plus One Query không phải mọi vấn đề performance database. Query chậm vì thiếu index, lock, full table scan hoặc network latency là vấn đề khác. N+1 tập trung vào pattern “loop sinh query” làm số query tăng tuyến tính theo số record.

## Core Mechanism / Cơ chế lõi

N+1 thường sinh ra từ lazy loading hoặc resolver gọi data access trong vòng lặp. Dữ liệu ít thì khó thấy lỗi, nhưng khi list dài hoặc traffic cao, query count tăng mạnh, connection pool bị áp lực, latency tăng và database bị quá tải vì nhiều round trip nhỏ.

## Project Role / Vai trò trong dự án

N Plus One Query là node cần mở khi API list page chậm, database query count tăng bất thường, ORM log có nhiều query giống nhau hoặc GraphQL endpoint chậm theo số item. Nó giúp team kiểm tra eager loading, join, batching, DataLoader, projection và query count test.

## Output / Artifact nên có

- Query count baseline cho endpoint/list page quan trọng
- ORM/logging config để thấy SQL được sinh ra
- Test hoặc performance check phát hiện query count tăng theo số item
- Fix note: eager loading, join, batch query, DataLoader hoặc projection phù hợp
- Benchmark trước/sau fix với số record đại diện production

## Decision Checklist / Câu hỏi kiểm tra

- Endpoint/list page có query trong vòng lặp không?
- ORM relation đang lazy load hay eager load?
- Query count có tăng theo số record trả về không?
- Có log SQL hoặc tracing để nhìn thấy nhiều query giống nhau không?
- Có thể fetch relation bằng join, include/eager load hoặc batch query không?
- GraphQL resolver có dùng DataLoader/batching không?
- Fix N+1 có làm payload quá lớn hoặc join quá nặng không?

## Failure Modes / Cách nó gây lỗi

- List page chạy ổn với dữ liệu demo nhưng chậm nặng khi production có nhiều record.
- Mỗi item trigger lazy load làm database nhận hàng trăm/hàng nghìn query nhỏ.
- Connection pool bị cạn vì nhiều request cùng tạo N+1 queries.
- Cache che lỗi trong dev nhưng cache miss ở production làm latency tăng đột biến.
- Fix bằng eager load quá rộng làm response nặng hoặc join sinh duplicate/Cartesian explosion.
- Không có query count test nên N+1 quay lại sau refactor.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset rất nhỏ và endpoint không nằm trên path quan trọng có thể chưa cần tối ưu ngay.
- Không nên eager load mọi relation mặc định vì có thể làm query/payload lớn hơn cần thiết.
- Với report/batch job ít chạy, giải pháp đơn giản có thể đủ nếu thời gian chạy chấp nhận được.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ORM]] vì lazy loading trong ORM là nguồn phổ biến gây N+1.
- [[Database Query]] vì cần nhìn số lượng và pattern query để phát hiện N+1.
- [[Connection Pooling]] vì N+1 tạo nhiều round trip và có thể làm pool cạn dưới tải.
- [[Latency]] vì N+1 thường biểu hiện thành response time tăng theo số item.

## Liên quan rộng

- Backend performance
- GraphQL resolver
- Query optimization
- API list endpoint

## Keywords / Từ khóa tìm kiếm

- N Plus One Query
- N+1 Query
- N+1 query
- truy vấn N cộng 1
- ORM lazy loading
- eager loading
- query count
- query in loop
- database round trip
- GraphQL N+1
- DataLoader
- batch loading
- API list slow
- SQL log nhiều query

## Source trace

- Hibernate documentation
- Rails ActiveRecord documentation
