# Distributed System

Aliases: distributed systems, hệ phân tán

Type: Architecture / System Design

## Context / Ngữ cảnh

Distributed System xuất hiện khi nhiều node hoặc process phối hợp qua network để cung cấp một service hoặc dữ liệu chung.

## Boundary / Ranh giới

### Nó là gì

Distributed System là hệ thống gồm nhiều thành phần chạy độc lập, giao tiếp qua network và có failure độc lập.

### Nó không phải là gì

Nó không chỉ là microservices và không tự tốt hơn monolith.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là communication + partial failure + coordination + consistency trade-off.

## Project Role / Vai trò trong dự án

Node này giúp reasoning về retry, consistency, latency, fault tolerance và operational complexity.

## Output / Artifact nên có

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- [[Fault Tolerance]]
- [[Leader Election]]
- [[Quorum]]
- [[CAP Theorem]]

## Nối mạnh

- [[Consistency]] vì distributed systems phải chọn consistency guarantees
- [[Replication]] vì replication là pattern phân tán phổ biến

## Liên quan rộng

- Partial failure
- Coordination

## Source trace

- Designing Data-Intensive Applications Part II
