# Bloom Filter

Aliases: Bloom Filter, probabilistic set filter

Type: Database Internals

## Context / Ngữ cảnh

Bloom Filter xuất hiện khi hệ thống cần kiểm tra nhanh “có thể tồn tại” hay “chắc chắn không tồn tại” trong tập dữ liệu lớn mà không muốn lookup đầy đủ.

## Boundary / Ranh giới

### Nó là gì

Bloom Filter là cấu trúc dữ liệu xác suất dùng nhiều hash function và bit array để test membership với false positive có thể xảy ra nhưng false negative không xảy ra nếu filter được dùng đúng.

### Nó không phải là gì

Bloom Filter không cho biết item chắc chắn có tồn tại. Nó chỉ nói “có thể có” hoặc “chắc chắn không có”.

## Core Mechanism / Cơ chế lõi

Khi insert item, nhiều hash function set các bit tương ứng. Khi query item, nếu bất kỳ bit nào chưa set thì item chắc chắn không có; nếu tất cả bit đã set thì item có thể có.

## Project Role / Vai trò trong dự án

Dùng node này khi debug storage engine, cache miss path, LSM tree, distributed system membership check hoặc query optimization dùng probabilistic filter.

## Output / Artifact nên có

- Expected item count
- False positive rate target
- Hash function/count setting
- Bit array size
- Metric: false positive, memory, lookup avoided

## Decision Checklist / Câu hỏi kiểm tra

- False positive rate chấp nhận được bao nhiêu?
- Filter có hỗ trợ delete không hay cần counting filter?
- Item count thực tế có vượt thiết kế không?
- False positive có gây cost hay correctness issue không?
- Filter được rebuild/rotate khi nào?

## Failure Modes / Cách nó gây lỗi

- Item count vượt dự kiến làm false positive tăng cao.
- Hiểu nhầm “possibly present” thành “definitely present”.
- Cần delete nhưng dùng Bloom filter thường.
- Hash/serialization không ổn định giữa producer và consumer.
- Filter stale làm hệ thống bỏ qua optimization mong đợi.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset nhỏ hoặc lookup rẻ thì Bloom filter không đáng thêm complexity.
- Không nên dùng Bloom filter nếu false positive gây hậu quả nghiệp vụ nghiêm trọng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cache]] vì Bloom filter có thể tránh lookup/cache miss tốn kém.
- [[Read Amplification]] vì filter thường giảm read amplification trong storage engine.
- [[Query Plan]] vì một số engine dùng filter để giảm candidate scan.
- [[Data Quality]] vì hash/serialization sai làm filter không đáng tin.

## Liên quan rộng

- Probabilistic data structure
- Membership test
- False positive

## Keywords / Từ khóa tìm kiếm

- Bloom Filter
- probabilistic set filter
- false positive
- membership test
- bit array
- hash function
- Bloom filter debugging

## Source trace

- Designing Data-Intensive Applications
- Database System Concepts
