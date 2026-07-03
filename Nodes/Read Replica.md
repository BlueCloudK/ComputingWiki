# Read Replica

Aliases: Read Replica, read replica, database replica, bản sao đọc

Type: Database Systems

## Context / Ngữ cảnh

Read Replica là node bổ sung cho ComputingWiki về bản sao database phục vụ đọc để giảm tải primary.

## Boundary / Ranh giới

### Nó là gì

Read Replica dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới bản sao database phục vụ đọc để giảm tải primary.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Read Replica là hiểu boundary, input/output, state và failure mode riêng của bản sao database phục vụ đọc để giảm tải primary.

## Project Role / Vai trò trong dự án

Read Replica giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Read Replica schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Read Replica ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Read Replica làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Read Replica nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Replication]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Read Replica

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Read Replica
- read replica
- database replica
- bản sao đọc
- read
- replica

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
