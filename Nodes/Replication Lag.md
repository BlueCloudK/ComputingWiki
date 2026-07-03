# Replication Lag

Aliases: Replication Lag, replication lag, replica delay, trễ replication

Type: Database Systems

## Context / Ngữ cảnh

Replication Lag là node bổ sung cho ComputingWiki về độ trễ giữa primary và replica khi dữ liệu chưa đồng bộ kịp.

## Boundary / Ranh giới

### Nó là gì

Replication Lag dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới độ trễ giữa primary và replica khi dữ liệu chưa đồng bộ kịp.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Replication Lag là hiểu boundary, input/output, state và failure mode riêng của độ trễ giữa primary và replica khi dữ liệu chưa đồng bộ kịp.

## Project Role / Vai trò trong dự án

Replication Lag giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Replication Lag schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Replication Lag ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Replication Lag làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Replication Lag nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Replication]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Replication Lag
- [[Read Replica]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Replication Lag

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Replication Lag
- replication lag
- replica delay
- trễ replication
- replication

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
