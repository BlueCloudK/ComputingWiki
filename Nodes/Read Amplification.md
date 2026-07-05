# Read Amplification

Aliases: Read Amplification, read amplification

Type: Database Internals

## Context / Ngữ cảnh

Read Amplification xuất hiện khi để trả một lượng dữ liệu logic nhỏ, storage engine/database phải đọc nhiều page/file/index/chunk hơn cần thiết.

## Boundary / Ranh giới

### Nó là gì

Read Amplification là tỷ lệ giữa dữ liệu thật sự cần đọc và lượng dữ liệu hệ thống phải đọc từ storage/cache/index để trả kết quả.

### Nó không phải là gì

Read Amplification không chỉ là query chậm chung chung. Nó chỉ ra chi phí đọc bị phình do layout, index, compaction, bloat, chunking hoặc access pattern.

## Core Mechanism / Cơ chế lõi

Query hoặc storage lookup đi qua index, page, SSTable, heap, cache hoặc file segment. Nếu dữ liệu liên quan nằm rải rác, stale/bloat nhiều hoặc filter yếu, hệ thống phải đọc nhiều candidate rồi mới bỏ đi.

## Project Role / Vai trò trong dự án

Dùng node này khi debug I/O cao, query scan quá nhiều page, LSM lookup đọc nhiều level, cache hit thấp hoặc RAG/vector store retrieve nhiều context nhiễu.

## Output / Artifact nên có

- Logical rows/bytes requested
- Physical pages/bytes read
- Query plan / storage trace
- Cache hit ratio
- Before/after index/layout comparison

## Decision Checklist / Câu hỏi kiểm tra

- Để trả result, hệ thống phải đọc bao nhiêu page/segment?
- Có bloat/stale data làm đọc thừa không?
- Index/filter có đủ selective không?
- Working set có bị vượt cache không?
- Layout hoặc compaction có giảm read amplification không?

## Failure Modes / Cách nó gây lỗi

- Query trả ít row nhưng đọc rất nhiều page.
- Bloat làm scan/index lookup đắt dần.
- Bloom/filter thiếu làm storage lookup nhiều file thừa.
- Chunk/context overlap quá lớn làm retrieval duplicate.
- Chỉ tối ưu CPU trong khi bottleneck thật là I/O đọc thừa.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset nhỏ nằm trong RAM có thể chưa thấy impact.
- Không nên tối ưu layout/index nếu metric chưa chứng minh read amplification là bottleneck.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Page Cache]] vì đọc thừa làm cache churn và giảm hit ratio.
- [[Storage Layout]] vì layout vật lý quyết định đọc bao nhiêu page.
- [[Bloom Filter]] vì filter có thể giảm lookup thừa.
- [[Query Plan]] vì plan thể hiện pages/rows được scan.

## Liên quan rộng

- Disk I/O
- Storage engine
- Cache efficiency

## Keywords / Từ khóa tìm kiếm

- Read Amplification
- read amplification
- physical read
- logical read
- cache churn
- storage lookup
- read amplification debugging

## Source trace

- Designing Data-Intensive Applications
- Database System Concepts
