# Cache

Aliases: caching, cache

Type: Data / Database

## Context / Ngữ cảnh

Cache xuất hiện khi hệ thống muốn lưu tạm kết quả đọc/tính toán ở nơi truy cập nhanh hơn source of truth để giảm latency, giảm tải database/API hoặc hấp thụ traffic spike. Nó thường nằm ở browser, CDN, reverse proxy, app memory, Redis/Memcached, database query cache hoặc computed result cache.

## Boundary / Ranh giới

### Nó là gì

Cache là lớp lưu dữ liệu phụ, thường có thể tái tạo từ source of truth. Cache tốt phải có key rõ, TTL/invalidation rõ, consistency expectation rõ và metric hit/miss rõ. Nó là trade-off giữa tốc độ/tải và độ tươi/độ đúng của dữ liệu.

### Nó không phải là gì

Cache không phải source of truth mặc định. Nếu cache mất mà dữ liệu không thể tái tạo, đó đã là storage/state quan trọng cần backup và durability khác. Cache cũng không sửa query/model sai tận gốc; nó chỉ giảm tần suất chạm bottleneck và có thể che lỗi cho tới khi traffic/cache miss xảy ra.

## Core Mechanism / Cơ chế lõi

Request kiểm tra cache theo key. Nếu hit, trả dữ liệu cached. Nếu miss, hệ thống đọc/tính từ source, ghi cache với TTL/version/policy rồi trả kết quả. Các pattern phổ biến gồm cache-aside, read-through, write-through, write-back, refresh-ahead và stale-while-revalidate.

## Project Role / Vai trò trong dự án

Cache ảnh hưởng tới latency, database load, API cost, consistency và debugging. Khi thiết kế cache, team cần biết dữ liệu nào được cache, key gồm gì, stale được bao lâu, invalidation xảy ra khi nào, hit rate có đáng không và cache miss có làm hệ thống chịu nổi không.

## Output / Artifact nên có

- Cache policy: key, value, TTL, invalidation, max size, eviction policy
- Consistency note: dữ liệu được phép stale bao lâu và impact nếu stale
- Metric: hit rate, miss rate, stale age, eviction, cache latency, backend load on miss
- Load test cho cache hit/miss và cold start
- Runbook cho cache flush, hot key, stale cache và cache stampede

## Decision Checklist / Câu hỏi kiểm tra

- Source of truth thật nằm ở đâu?
- Cache key có chứa đủ tenant/user/permission/version không?
- Dữ liệu này được phép stale bao lâu?
- Khi source data update/delete, cache invalidate bằng TTL, event hay delete-on-write?
- Cache miss/cold start có làm backend quá tải không?
- Có cần cache negative result hoặc chống cache penetration không?
- Có metric để biết cache đang giúp hay đang gây lỗi không?

## Failure Modes / Cách nó gây lỗi

- Cache key thiếu tenant/user làm lộ dữ liệu giữa người dùng.
- TTL quá dài hoặc invalidation fail làm stale cache.
- Hot key hết hạn làm cache stampede và đánh sập database.
- Cache quá lớn hoặc không eviction làm cạn memory.
- Cache flush toàn bộ làm backend nhận traffic thật đột ngột.
- Cache hit rate cao che query chậm, tới lúc miss/cold start thì production sập.

## Khi nào chưa cần hoặc dễ over-engineer

- Data nhỏ, query rẻ hoặc traffic thấp có thể chưa cần cache.
- Không nên cache trước khi biết bottleneck thật và freshness requirement.
- Không nên cache dữ liệu security-sensitive nếu không có key/scope/invalidation cực rõ.

## Gồm những gì

- [[Index]]

## Nối mạnh

- [[Stale Cache]] vì stale data là failure mode trực tiếp của cache.
- [[Cache Stampede]] vì hot key/cache miss đồng loạt có thể làm backend quá tải.
- [[CDN]] vì CDN là cache layer phổ biến ở edge/browser-facing path.
- [[Backpressure]] vì cache miss storm cần cơ chế bảo vệ backend.
- [[Redis]] vì Redis thường được dùng làm distributed cache.

## Liên quan rộng

- Performance optimization
- Data freshness
- Read scalability
- System reliability

## Keywords / Từ khóa tìm kiếm

- Cache
- caching
- cache key
- cache hit
- cache miss
- TTL
- cache invalidation
- cache aside
- read through cache
- write through cache
- stale while revalidate
- hot key
- cache eviction
- distributed cache
- cache debugging

## Source trace

- Designing Data-Intensive Applications
- Caching pattern references
