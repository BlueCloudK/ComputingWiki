# Check Constraint

Aliases: Check Constraint, check constraint, SQL check, ràng buộc kiểm tra

Type: Database Systems

## Context / Ngữ cảnh

Check Constraint là node bổ sung cho ComputingWiki về constraint đảm bảo giá trị trong row thỏa điều kiện logic.

## Boundary / Ranh giới

### Nó là gì

Check Constraint dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới constraint đảm bảo giá trị trong row thỏa điều kiện logic.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng Database Systems; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Check Constraint là hiểu boundary, input/output, state và failure mode riêng của constraint đảm bảo giá trị trong row thỏa điều kiện logic.

## Project Role / Vai trò trong dự án

Check Constraint giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Check Constraint schema/query/operation note
- Migration hoặc rollback plan nếu ảnh hưởng dữ liệu
- Metric như latency, lock wait, storage hoặc replication lag khi có

## Decision Checklist / Câu hỏi kiểm tra

- Check Constraint ảnh hưởng read, write, consistency hay storage?
- Có impact tới migration/backup/restore không?
- Có query plan, constraint hoặc test dữ liệu để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Check Constraint làm mất dữ liệu, chậm query hoặc sai consistency
- Thiếu migration/rollback làm deploy database rủi ro
- Không đo metric khiến bottleneck chỉ lộ khi dữ liệu lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Check Constraint nếu dữ liệu nhỏ và query đơn giản
- Dễ over-engineer nếu tối ưu database trước khi có workload thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Integrity Constraint]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Check Constraint

## Liên quan rộng

- Database internals
- Data modeling
- Operational data

## Keywords / Từ khóa tìm kiếm

- Check Constraint
- check constraint
- SQL check
- ràng buộc kiểm tra
- check
- constraint

## Source trace

- Database System Concepts
- Designing Data-Intensive Applications
- PostgreSQL documentation
