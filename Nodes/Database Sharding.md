# Database Sharding

Aliases: Database Sharding, sharding, database sharding, chia shard

Type: Database Systems

## Context / Ngữ cảnh

Database Sharding là node bổ sung cho ComputingWiki về chia dữ liệu ngang qua nhiều database/node theo shard key.

## Boundary / Ranh giới

### Nó là gì

Database Sharding dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới chia dữ liệu ngang qua nhiều database/node theo shard key.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Database Sharding là hiểu boundary, input/output, state và failure mode riêng của chia dữ liệu ngang qua nhiều database/node theo shard key.

## Project Role / Vai trò trong dự án

Database Sharding giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Database Sharding schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Database Sharding ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Database Sharding làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Database Sharding nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Partitioning]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Database Sharding
- [[Scalability]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Database Sharding

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Database Sharding
- sharding
- database sharding
- chia shard
- database

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
