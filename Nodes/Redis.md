# Redis

Aliases: Redis, Redis cache, in-memory data store

Type: Cache / Data Store

## Context / Ngữ cảnh

Redis xuất hiện khi hệ thống cần một data store trong memory cho cache, session, rate limit counter, queue nhẹ, pub/sub, distributed lock đơn giản hoặc ephemeral coordination. Nó thường được thêm vào backend để giảm latency và giảm tải database, nhưng cũng tạo thêm consistency và operations risk.

## Boundary / Ranh giới

### Nó là gì

Redis là in-memory data structure server hỗ trợ key-value, string, hash, list, set, sorted set, stream, TTL, atomic command, replication và persistence option. Redis rất nhanh cho access pattern đơn giản, counter, cache key và data structure nhỏ/nhanh.

### Nó không phải là gì

Redis không mặc định thay thế database chính cho dữ liệu cần durability, transaction phức tạp, relational constraint hoặc recovery chắc chắn. Nếu dùng Redis như source of truth nhưng không có persistence/backup/failover plan, sự cố Redis có thể thành mất dữ liệu thật.

## Core Mechanism / Cơ chế lõi

Client gửi command tới Redis server. Redis giữ data trong memory, xử lý command nhanh, có thể expire key theo TTL và evict key khi memory chạm limit tùy policy. Persistence như RDB/AOF và replication/failover có thể bật nhưng cần cấu hình rõ theo nhu cầu cache hay state quan trọng.

## Project Role / Vai trò trong dự án

Redis là node cần mở khi debug cache invalidation, session expiry, rate limit sai, distributed lock hết hạn, queue backlog, memory pressure, eviction hoặc Redis down làm app fail. Nó giúp team quyết định key naming, TTL, eviction, persistence, fallback và metric cần theo dõi.

## Output / Artifact nên có

- Redis usage inventory: cache, session, rate limit, queue, lock hay pub/sub
- Key naming convention và TTL policy
- Memory/eviction config: maxmemory, eviction policy, expected key volume
- Persistence/failover decision nếu dữ liệu không thể mất
- Metric dashboard: memory, ops/sec, latency, evicted keys, expired keys, hit rate, connected clients
- Runbook cho Redis down, memory full, eviction spike và slow command

## Decision Checklist / Câu hỏi kiểm tra

- Key này là cache mất được hay state quan trọng?
- TTL có đúng business expectation không?
- Eviction policy có thể xóa session/lock/counter quan trọng không?
- Redis down thì app degrade, bypass cache hay fail cứng?
- Có key namespace theo environment/tenant/service để tránh collision không?
- Dữ liệu có cần persistence/replication/backup không?
- Command/pattern có nguy cơ block hoặc scan toàn keyspace không?

## Failure Modes / Cách nó gây lỗi

- Cache stale làm user thấy dữ liệu cũ hoặc quyền cũ.
- Memory full/eviction xóa session, rate limit counter hoặc lock quan trọng.
- Dùng Redis làm durable database rồi mất dữ liệu khi restart/failover/config sai.
- Key naming thiếu namespace làm service này ghi đè key service khác.
- Distributed lock TTL sai làm hai worker cùng xử lý một job/resource.
- Dùng blocking/expensive command trên production làm latency spike.
- Redis down nhưng app không fallback làm toàn bộ request fail dù database chính vẫn khỏe.

## Khi nào chưa cần hoặc dễ over-engineer

- Database hiện tại đáp ứng latency/tải và không có bottleneck rõ thì chưa cần Redis.
- Không nên thêm cache trước khi có invalidation plan và hit/miss metric.
- Không nên dùng Redis cho queue/lock quan trọng nếu team chưa hiểu failure/retry/fencing behavior.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì Redis thường được dùng làm distributed cache.
- [[Rate Limiting]] vì Redis hay lưu counter/window/token bucket cho rate limit.
- [[Session Management]] vì Redis thường làm session store trong web backend.
- [[Stale Cache]] vì Redis cache có thể stale nếu TTL/invalidation sai.
- [[Resource Exhaustion]] vì Redis memory full/eviction là một dạng cạn tài nguyên.

## Liên quan rộng

- Session store
- Queue
- Distributed lock
- Pub/Sub
- In-memory data store

## Keywords / Từ khóa tìm kiếm

- Redis
- Redis cache
- in-memory data store
- TTL
- eviction policy
- maxmemory
- session store
- pub/sub
- Redis streams
- rate limit counter
- distributed lock
- Redis persistence
- RDB
- AOF
- Redis debugging

## Source trace

- Redis official documentation
