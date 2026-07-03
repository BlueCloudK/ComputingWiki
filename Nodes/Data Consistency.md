# Data Consistency

Aliases: Data Consistency, data consistency, consistent data, nhất quán dữ liệu

Type: Database Systems

## Context / Ngữ cảnh

Data Consistency là node bổ sung cho ComputingWiki về mức dữ liệu quan sát được có đúng và đồng bộ theo rule hệ thống không.

## Boundary / Ranh giới

### Nó là gì

Data Consistency dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới mức dữ liệu quan sát được có đúng và đồng bộ theo rule hệ thống không.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Data Consistency là hiểu boundary, input/output, state và failure mode riêng của mức dữ liệu quan sát được có đúng và đồng bộ theo rule hệ thống không.

## Project Role / Vai trò trong dự án

Data Consistency giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Data Consistency schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Data Consistency ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Data Consistency làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Data Consistency nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Consistency]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Data Consistency
- [[Transaction]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Data Consistency

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Data Consistency
- data consistency
- consistent data
- nhất quán dữ liệu
- data
- consistency

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
