# Query Planner

Aliases: Query Planner, query planner, SQL planner, bộ lập kế hoạch truy vấn

Type: Database Systems

## Context / Ngữ cảnh

Query Planner là node bổ sung cho ComputingWiki về thành phần chọn query plan dựa trên statistics và cost estimate.

## Boundary / Ranh giới

### Nó là gì

Query Planner dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới thành phần chọn query plan dựa trên statistics và cost estimate.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Query Planner là hiểu boundary, input/output, state và failure mode riêng của thành phần chọn query plan dựa trên statistics và cost estimate.

## Project Role / Vai trò trong dự án

Query Planner giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Query Planner schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Query Planner ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Query Planner làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Query Planner nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Query Optimizer]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Query Planner
- [[Query Plan]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Query Planner

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Query Planner
- query planner
- SQL planner
- bộ lập kế hoạch truy vấn
- query
- planner

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
