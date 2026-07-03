# Redis

Aliases: Redis, Redis cache, in-memory data store

Type: Cache / Data Store

## Context / Ngữ cảnh

Redis là in-memory data store thường dùng cho cache, session, rate limit, queue nhẹ, pub/sub và distributed coordination đơn giản.

## Boundary / Ranh giới

### Nó là gì

Nó là key-value/data-structure server chạy trong memory, hỗ trợ TTL, persistence option, replication và atomic command.

### Nó không phải là gì

Nó không thay thế database chính nếu dữ liệu cần durability/transaction phức tạp và recovery chắc chắn.

## Core Mechanism / Cơ chế lõi

Redis lưu key/value hoặc data structure trong memory, xử lý command nhanh, dùng TTL/eviction để quản lý cache và có persistence/replication tùy config.

## Project Role / Vai trò trong dự án

Node này giúp debug cache invalidation, session expiry, rate limit, lock tạm, queue backlog và memory pressure.

## Output / Artifact nên có

- Key naming và TTL policy
- Eviction/memory config
- Cache invalidation hoặc session expiry rule

## Decision Checklist / Câu hỏi kiểm tra

- Key này là cache mất được hay state quan trọng?
- TTL có đúng với business expectation không?
- Eviction policy có thể xóa dữ liệu đang cần không?
- Redis down thì app degrade hay fail cứng?

## Failure Modes / Cách nó gây lỗi

- Cache stale làm user thấy dữ liệu cũ
- Memory full/eviction xóa session hoặc lock quan trọng
- Dùng Redis như database durable rồi mất dữ liệu khi failover/config sai

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Redis nếu database hiện tại đáp ứng latency và tải
- Dễ over-engineer nếu thêm cache trước khi đo bottleneck hoặc có invalidation plan

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì Redis thường được dùng như cache layer
- [[Rate Limiting]] vì Redis hay lưu counter/window cho rate limit

## Liên quan rộng

- Session store
- Queue
- Distributed lock

## Keywords / Từ khóa tìm kiếm

- Redis
- Redis cache
- in-memory data store
- TTL
- eviction policy
- session store
- pub/sub
- rate limit counter

## Source trace

- Redis official documentation
