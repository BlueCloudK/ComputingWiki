# Referential Integrity

Aliases: Referential Integrity, referential integrity, foreign key integrity, toàn vẹn tham chiếu

Type: Database Systems

## Context / Ngữ cảnh

Referential Integrity là node bổ sung cho ComputingWiki về ràng buộc đảm bảo quan hệ giữa bảng không trỏ tới dữ liệu không tồn tại.

## Boundary / Ranh giới

### Nó là gì

Referential Integrity dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới ràng buộc đảm bảo quan hệ giữa bảng không trỏ tới dữ liệu không tồn tại.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Referential Integrity là hiểu boundary, input/output, state và failure mode riêng của ràng buộc đảm bảo quan hệ giữa bảng không trỏ tới dữ liệu không tồn tại.

## Project Role / Vai trò trong dự án

Referential Integrity giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Referential Integrity schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Referential Integrity ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Referential Integrity làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Referential Integrity nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Foreign Key]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Referential Integrity
- [[Integrity Constraint]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Referential Integrity

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Referential Integrity
- referential integrity
- foreign key integrity
- toàn vẹn tham chiếu
- referential
- integrity

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
