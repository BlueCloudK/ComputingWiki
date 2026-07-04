# CDN

Aliases: Content Delivery Network, mạng phân phối nội dung

Type: Architecture / System Design

## Context / Ngữ cảnh

CDN xuất hiện khi static asset, media, web page hoặc cacheable API response cần được phục vụ gần user hơn để giảm latency, bandwidth cost và tải lên origin. Nó thường dùng cho JS/CSS/image/video, file download, website content, edge caching và DDoS/traffic spike absorption.

## Boundary / Ranh giới

### Nó là gì

CDN là mạng edge proxy/cache đặt ở nhiều location. User request tới edge gần nhất; edge trả cache hit nếu có, hoặc fetch từ origin rồi cache theo policy. CDN có thể xử lý HTTPS, compression, HTTP/2/3, cache key, purge/invalidation, WAF/rule và origin shield tùy provider.

### Nó không phải là gì

CDN không phải database cache và không tự sửa API/app chậm nếu content không cache được. CDN cũng không an toàn mặc định cho dữ liệu private; nếu cache key/header/cookie sai, CDN có thể cache response user này rồi trả cho user khác.

## Core Mechanism / Cơ chế lõi

CDN quyết định cache dựa trên URL, method, headers, cookies, query string, cache-control, TTL và custom cache key. Khi miss, edge gọi origin. Khi hit, edge trả response từ cache. Deploy content mới cần cache-busting filename hoặc purge/invalidation để tránh stale asset.

## Project Role / Vai trò trong dự án

CDN là node cần mở khi website có static assets lớn, user ở nhiều vùng, origin bị tải nặng, asset stale sau deploy hoặc frontend bundle/API response bị cache sai. Nó giúp team thiết kế cache policy, origin fallback, HTTPS, invalidation và observability theo edge/origin.

## Output / Artifact nên có

- CDN cache policy: TTL, cache key, query/header/cookie behavior, private/public rule
- Origin config: domain, HTTPS, origin shield/fallback, timeout
- Invalidation/purge plan hoặc asset fingerprinting strategy
- Security note: không cache private response, signed URL/cookie nếu cần
- Metrics/log: cache hit ratio, origin fetch, edge latency, 4xx/5xx, purge events

## Decision Checklist / Câu hỏi kiểm tra

- Content này public/cacheable hay user-specific/private?
- Cache key có phân biệt auth, language, device, query và version đúng không?
- Deploy asset mới dùng hashed filename hay cần purge CDN?
- Origin có chịu được cache miss/cold start không?
- CDN có forward đúng headers/cookies cần thiết không?
- HTTPS terminate ở CDN và origin connection có an toàn không?
- Khi CDN cache sai, có cách purge nhanh và audit không?

## Failure Modes / Cách nó gây lỗi

- Cache private response làm user khác thấy dữ liệu không thuộc quyền.
- Stale JS/CSS sau deploy làm frontend chạy version cũ với API mới.
- Cache key thiếu language/device/query làm user nhận content sai biến thể.
- TTL quá thấp làm CDN không giảm tải origin đáng kể.
- TTL quá cao hoặc purge chậm làm fix production không tới user kịp.
- CDN che lỗi origin vì edge vẫn hit cache, làm monitoring origin/user impact lệch nhau.

## Khi nào chưa cần hoặc dễ over-engineer

- Traffic nhỏ, user gần origin hoặc content không cacheable có thể chưa cần CDN.
- Không nên đưa API dynamic/private qua CDN nếu chưa có cache key và security policy rõ.
- Không nên dùng CDN để che origin quá chậm mà không hiểu cache miss behavior.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì CDN là cache layer ở network edge.
- [[Stale Cache]] vì CDN stale asset/content là failure mode phổ biến.
- [[SPA]] vì SPA static bundle thường được phục vụ qua CDN.
- [[HTTPS]] vì CDN thường terminate/proxy HTTPS.
- [[Load Balancer]] vì CDN/edge thường đứng trước origin/LB trong traffic path.

## Liên quan rộng

- Edge delivery
- Static assets
- Web performance
- Origin protection

## Keywords / Từ khóa tìm kiếm

- CDN
- Content Delivery Network
- mạng phân phối nội dung
- edge cache
- static asset delivery
- cache hit ratio
- origin fetch
- cache key
- cache-control
- CDN purge
- CDN invalidation
- asset fingerprinting
- origin shield
- signed URL
- CDN debugging

## Source trace

- Computer Networks Map
- Cloud architecture documentation
