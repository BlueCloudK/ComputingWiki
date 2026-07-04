# Cache Stampede

Aliases: cache miss storm, stampede cache

Type: Failure Pattern

## Context / Ngữ cảnh

Cache Stampede xuất hiện khi một key nóng hết hạn hoặc bị miss, rồi nhiều request đồng thời cùng tính lại dữ liệu hoặc cùng gọi backend/database cho cùng một nội dung. Nó thường xảy ra ở trang/homepage hot, API read-heavy, recommendation, config lookup, pricing hoặc dữ liệu cache có TTL giống nhau.

## Boundary / Ranh giới

### Nó là gì

Cache Stampede là failure pattern trong đó cache không còn hấp thụ traffic mà biến một miss thành nhiều request backend đồng thời. Vấn đề không chỉ là cache miss, mà là nhiều caller cùng miss một key/tập key và cùng tái tạo dữ liệu nặng cùng lúc.

### Nó không phải là gì

Cache Stampede không phải mọi lỗi cache. Stale cache là dữ liệu cũ; cache penetration là request key không tồn tại; cache avalanche là nhiều key hết hạn cùng lúc. Stampede tập trung vào hot key hoặc hot data bị nhiều request tái tính đồng thời.

## Core Mechanism / Cơ chế lõi

Khi cache key hết hạn, request đầu tiên lẽ ra tái tạo dữ liệu rồi ghi lại cache. Nếu không có lock, request coalescing hoặc stale-while-revalidate, tất cả request đồng thời đều gọi database/service gốc. Backend bị spike tải, latency tăng, timeout/retry xảy ra và có thể kéo theo outage dây chuyền.

## Project Role / Vai trò trong dự án

Cache Stampede là node cần mở khi hệ thống read-heavy đột nhiên làm database/API gốc quá tải đúng lúc cache hết hạn hoặc deploy clear cache. Nó giúp team thiết kế TTL jitter, singleflight/request coalescing, lock, prewarm, stale-while-revalidate và metric theo hot key.

## Output / Artifact nên có

- Cache policy cho hot key: TTL, jitter, stale time, refresh strategy
- Request coalescing/singleflight hoặc distributed lock design
- Metric: cache hit rate, miss rate, backend load on miss, hot key frequency, regeneration latency
- Load test mô phỏng nhiều request đồng thời khi cache expired
- Runbook cho cache flush, hot key spike và backend overload do cache miss

## Decision Checklist / Câu hỏi kiểm tra

- Key nào là hot key và backend cost khi miss là bao nhiêu?
- TTL của nhiều key có bị align cùng lúc không?
- Khi một key miss, có singleflight/lock để chỉ một request rebuild không?
- Có dùng stale-while-revalidate hoặc serve stale khi backend chậm không?
- Cache warm/preload có cần cho release hoặc traffic spike không?
- Retry sau miss có làm backend bị nhân tải không?
- Metric có thấy miss storm theo key cụ thể không?

## Failure Modes / Cách nó gây lỗi

- Hot key hết hạn làm hàng nghìn request cùng query database.
- TTL giống nhau cho nhiều key làm nhiều key hết hạn cùng lúc sau deploy/warmup.
- Distributed lock sai làm lock contention hoặc deadlock ở cache layer.
- Serve stale không có giới hạn làm user thấy dữ liệu quá cũ.
- Cache flush toàn bộ làm backend nhận traffic thật đột ngột.
- Retry/timeout khi rebuild cache làm miss storm kéo dài hơn.

## Khi nào chưa cần hoặc dễ over-engineer

- Traffic thấp hoặc dữ liệu rebuild rất rẻ có thể chỉ cần TTL đơn giản.
- Không nên thêm distributed lock phức tạp nếu single instance/singleflight local đã đủ.
- Không nên cache mọi thứ trước khi biết key nào hot và backend cost nào đáng giảm.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì stampede là failure mode trực tiếp của cache under load.
- [[Stale Cache]] vì stale-while-revalidate là một cách giảm stampede nhưng có trade-off dữ liệu cũ.
- [[Backpressure]] vì cần hạn chế tải backend khi cache miss storm xảy ra.
- [[Retry]] vì retry sai có thể làm stampede nặng hơn.

## Liên quan rộng

- High-traffic backend
- Read scalability
- Database protection
- CDN caching

## Keywords / Từ khóa tìm kiếm

- Cache Stampede
- cache miss storm
- stampede cache
- hot key
- cache hot key
- TTL jitter
- request coalescing
- singleflight
- distributed lock
- stale while revalidate
- cache prewarm
- cache avalanche
- cache penetration
- miss storm
- cache stampede debugging

## Source trace

- Caching pattern references
- Cloudflare cache documentation
