# Page Cache

Aliases: Page Cache, buffer cache

Type: Database Internals

## Context / Ngữ cảnh

Page Cache xuất hiện khi database hoặc operating system giữ page/block dữ liệu trong memory để giảm disk I/O khi query đọc lại dữ liệu.

## Boundary / Ranh giới

### Nó là gì

Page Cache là lớp cache ở mức page/block, lưu dữ liệu đã đọc từ disk để lần đọc sau có thể lấy từ memory nhanh hơn.

### Nó không phải là gì

Page Cache không giống application cache theo key nghiệp vụ. Nó cache page storage thấp hơn, thường không biết ý nghĩa domain của dữ liệu.

## Core Mechanism / Cơ chế lõi

Khi query đọc table/index page, database hoặc OS nạp page từ disk vào memory. Page được giữ lại theo eviction policy; nếu query đọc lại page đó, hệ thống tránh được disk read.

## Project Role / Vai trò trong dự án

Dùng node này khi debug query lần đầu chậm lần sau nhanh, I/O bottleneck, buffer hit ratio, working set vượt RAM hoặc benchmark bị sai do warm cache.

## Output / Artifact nên có

- Buffer/page cache hit ratio
- Working set estimate
- Cold vs warm benchmark
- I/O read metric
- Query plan with buffer stats

## Decision Checklist / Câu hỏi kiểm tra

- Query đang cold cache hay warm cache?
- Working set có vừa RAM không?
- Buffer hit ratio có giảm khi tải tăng không?
- Bottleneck là disk I/O hay CPU/query plan?
- Benchmark có clear/kiểm soát cache không?

## Failure Modes / Cách nó gây lỗi

- Benchmark warm cache làm tưởng query nhanh hơn production cold path.
- Working set vượt RAM làm cache churn.
- Read amplification làm nhiều page cache bị đọc vô ích.
- OS cache và DB buffer cache bị hiểu lẫn.
- Tối ưu query trong khi bottleneck thật là cache miss/I/O.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset nhỏ nằm hết trong RAM thì page cache ít là vấn đề.
- Không nên chỉnh memory/cache setting nếu chưa có hit ratio và I/O metric.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Storage Layout]] vì page cache lưu page/block theo layout vật lý.
- [[Query Plan]] vì plan quyết định đọc bao nhiêu page.
- [[Read Amplification]] vì đọc nhiều page thừa làm cache/I/O tệ.
- [[Performance Optimization]] vì cache hit ảnh hưởng latency mạnh.

## Liên quan rộng

- Buffer pool
- Disk I/O
- Working set
- Cache hit ratio

## Keywords / Từ khóa tìm kiếm

- Page Cache
- buffer cache
- buffer pool
- cache hit ratio
- cold cache
- warm cache
- page cache debugging

## Source trace

- Database System Concepts
- PostgreSQL documentation
- Designing Data-Intensive Applications
