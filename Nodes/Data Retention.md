# Data Retention

Aliases: Data Retention, data retention, retention policy, lưu giữ dữ liệu

Type: Database Systems

## Context / Ngữ cảnh

Data Retention là node bổ sung cho ComputingWiki về quy tắc giữ dữ liệu trong bao lâu trước khi xóa hoặc archive.

## Boundary / Ranh giới

### Nó là gì

Data Retention dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới quy tắc giữ dữ liệu trong bao lâu trước khi xóa hoặc archive.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Data Retention là hiểu boundary, input/output, state và failure mode riêng của quy tắc giữ dữ liệu trong bao lâu trước khi xóa hoặc archive.

## Project Role / Vai trò trong dự án

Data Retention giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Data Retention schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Data Retention ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Data Retention làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Data Retention nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Quality]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Data Retention

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Data Retention
- data retention
- retention policy
- lưu giữ dữ liệu
- data
- retention

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
