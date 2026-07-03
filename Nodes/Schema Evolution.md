# Schema Evolution

Aliases: Schema Evolution, schema evolution, evolve schema, tiến hóa schema

Type: Database Systems

## Context / Ngữ cảnh

Schema Evolution là node bổ sung cho ComputingWiki về quá trình thay đổi schema theo thời gian mà vẫn giữ compatibility.

## Boundary / Ranh giới

### Nó là gì

Schema Evolution dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới quá trình thay đổi schema theo thời gian mà vẫn giữ compatibility.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Schema Evolution là hiểu boundary, input/output, state và failure mode riêng của quá trình thay đổi schema theo thời gian mà vẫn giữ compatibility.

## Project Role / Vai trò trong dự án

Schema Evolution giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Schema Evolution schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Schema Evolution ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Schema Evolution làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Schema Evolution nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Database Migration]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Schema Evolution
- [[Encoding and Evolution]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Schema Evolution

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Schema Evolution
- schema evolution
- evolve schema
- tiến hóa schema
- schema
- evolution

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
