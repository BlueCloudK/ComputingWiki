# CDN

Aliases: Content Delivery Network, mạng phân phối nội dung

Type: Architecture / System Design

## Context / Ngữ cảnh

CDN xuất hiện khi static/media/web content cần được phục vụ gần user hơn và giảm tải origin.

## Boundary / Ranh giới

### Nó là gì

CDN là mạng edge cache/proxy phân phối content từ location gần user.

### Nó không phải là gì

Nó không phải database cache và không tự sửa API chậm.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là cache/serve content từ edge dựa trên URL, headers và invalidation policy.

## Project Role / Vai trò trong dự án

Node này giúp cải thiện latency/bandwidth cho asset và bảo vệ origin khỏi traffic spike.

## Output / Artifact nên có

- Cache policy: TTL, key, headers
- Invalidation/purge plan
- Origin fallback và HTTPS config

## Decision Checklist / Câu hỏi kiểm tra

- Content này public/cacheable không?
- Cache key có phân biệt auth/language/device đúng không?
- Invalidation khi deploy content mới thế nào?

## Failure Modes / Cách nó gây lỗi

- Cache private response cho user khác
- Stale asset sau deploy
- CDN che lỗi origin vì cache hit

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu traffic nhỏ hoặc content không cache được
- Dễ over-engineer nếu API dynamic bị ép qua CDN không có cache strategy

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì CDN là cache ở network edge
- [[HTTPS]] vì CDN thường terminate/proxy HTTPS

## Liên quan rộng

- Edge delivery
- Static assets

## Keywords / Từ khóa tìm kiếm

- CDN
- Content Delivery Network
- edge cache
- static asset delivery
- cache hit
- origin shield
- mạng phân phối nội dung

## Source trace

- Computer Networks Map
- Cloud architecture docs
