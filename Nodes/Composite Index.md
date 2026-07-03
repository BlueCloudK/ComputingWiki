# Composite Index

Aliases: Composite Index, composite index, multi-column index, chỉ mục nhiều cột

Type: Database Systems

## Context / Ngữ cảnh

Composite Index là node bổ sung cho ComputingWiki về index gồm nhiều cột theo thứ tự cụ thể.

## Boundary / Ranh giới

### Nó là gì

Composite Index dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới index gồm nhiều cột theo thứ tự cụ thể.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Composite Index là hiểu boundary, input/output, state và failure mode riêng của index gồm nhiều cột theo thứ tự cụ thể.

## Project Role / Vai trò trong dự án

Composite Index giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Composite Index schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Composite Index ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Composite Index làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Composite Index nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Index]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Composite Index

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Composite Index
- composite index
- multi-column index
- chỉ mục nhiều cột
- composite
- index

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
