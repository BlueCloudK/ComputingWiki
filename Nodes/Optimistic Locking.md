# Optimistic Locking

Aliases: Optimistic Locking, optimistic locking, version column, khóa lạc quan

Type: Database Systems

## Context / Ngữ cảnh

Optimistic Locking là node bổ sung cho ComputingWiki về cách xử lý concurrency bằng version/check khi commit thay vì lock sớm.

## Boundary / Ranh giới

### Nó là gì

Optimistic Locking dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cách xử lý concurrency bằng version/check khi commit thay vì lock sớm.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Optimistic Locking là hiểu boundary, input/output, state và failure mode riêng của cách xử lý concurrency bằng version/check khi commit thay vì lock sớm.

## Project Role / Vai trò trong dự án

Optimistic Locking giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Optimistic Locking schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Optimistic Locking ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Optimistic Locking làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Optimistic Locking nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Concurrency Control]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Optimistic Locking

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Optimistic Locking
- optimistic locking
- version column
- khóa lạc quan
- optimistic
- locking

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
