# Stale Cache

Aliases: stale cached data, cache cũ

Type: Failure Pattern

## Context / Ngữ cảnh

Stale Cache xuất hiện khi cache trả về dữ liệu đã lỗi thời so với source of truth. Nó thường gặp trong API cache, CDN, Redis/memory cache, browser cache, RAG index/cache, permission cache, config cache hoặc computed result cache có TTL/invalidation không khớp nghiệp vụ.

## Boundary / Ranh giới

### Nó là gì

Stale Cache là failure pattern trong đó dữ liệu cache vẫn được dùng sau khi source data đã thay đổi hoặc quyền truy cập đã đổi. Staleness có thể chấp nhận được nếu được thiết kế rõ, nhưng trở thành lỗi khi user thấy dữ liệu sai, quyền cũ còn hiệu lực, hoặc decision dựa trên state không còn đúng.

### Nó không phải là gì

Stale Cache không phải cache miss hoặc cache stampede. Cache miss là không có dữ liệu cache; stampede là nhiều request cùng rebuild cache; stale cache là có cache nhưng cache cũ/sai. Một số cache cố ý stale trong vài giây/phút để đổi lấy performance, nhưng phải có boundary rõ.

## Core Mechanism / Cơ chế lõi

Cache lấy dữ liệu từ source of truth rồi lưu theo key, TTL, version hoặc invalidation event. Stale xảy ra khi TTL quá dài, invalidation miss, key không chứa version/tenant/permission, write path không update cache, hoặc hệ thống async làm cache/index update chậm hơn dữ liệu gốc.

## Project Role / Vai trò trong dự án

Stale Cache là node cần mở khi user thấy dữ liệu cũ sau update, permission vừa thu hồi nhưng vẫn còn hiệu lực, CDN trả asset cũ, hoặc RAG trả tài liệu đã bị sửa/xóa. Nó giúp team review cache key, TTL, invalidation, versioning, consistency expectation và monitoring stale age.

## Output / Artifact nên có

- Cache consistency note: dữ liệu nào được phép stale bao lâu
- Cache key design: tenant/user/permission/version/source id
- Invalidation strategy: TTL, event-based, write-through, delete-on-write, versioned key
- Stale age metric hoặc audit log cho dữ liệu nhạy cảm
- Test case update source rồi đọc lại qua cache, permission change và delete path

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu này được phép stale trong bao lâu?
- Cache key có chứa đủ tenant/user/scope/version không?
- Khi source data update/delete, cache được update, invalidate hay chờ TTL?
- Permission/security-sensitive data có được cache không, và revoke xử lý thế nào?
- Có nhiều lớp cache như browser/CDN/app/Redis gây stale khó trace không?
- Có metric/log cho cache hit kèm version/age không?
- Khi stale xảy ra, user impact là hiển thị sai, action sai hay data leak?

## Failure Modes / Cách nó gây lỗi

- User cập nhật profile/order nhưng API vẫn trả dữ liệu cũ từ cache.
- Permission bị thu hồi nhưng cache authorization vẫn cho truy cập.
- CDN/browser cache giữ asset cũ sau deploy làm frontend lỗi phiên bản.
- Cache key thiếu tenant/user làm dữ liệu user này lẫn sang user khác.
- RAG/vector index chưa update nên model trích dẫn tài liệu đã lỗi thời.
- Invalidation event fail âm thầm khiến cache cũ tồn tại tới hết TTL dài.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu read-only hoặc hiếm thay đổi có thể dùng TTL đơn giản.
- Không nên xây invalidation phức tạp nếu product chấp nhận stale rõ ràng và TTL ngắn đủ.
- Không nên cache permission/security-sensitive state nếu không có revoke/invalidation chắc chắn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì stale cache là failure mode trực tiếp của cache.
- [[Cache Stampede]] vì stale-while-revalidate giảm stampede nhưng tạo trade-off stale data.
- [[CDN]] vì CDN cache thường gây stale asset/content nếu invalidation sai.
- [[RAG]] vì stale corpus/index có thể làm AI trả lời bằng dữ liệu cũ.
- [[Access Control]] vì cache quyền cũ có thể thành lỗi bảo mật.

## Liên quan rộng

- Cache invalidation
- Eventual consistency
- Web deployment
- Data freshness

## Keywords / Từ khóa tìm kiếm

- Stale Cache
- stale cached data
- cache cũ
- cache invalidation
- cache freshness
- stale while revalidate
- TTL
- versioned cache key
- cache age
- cache consistency
- stale permission cache
- CDN stale cache
- stale RAG index
- cache debugging
- data freshness

## Source trace

- Designing Data-Intensive Applications
- Caching documentation references
