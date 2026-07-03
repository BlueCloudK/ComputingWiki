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

- System boundary diagram gồm node, network, datastore
- Failure-mode matrix cho timeout, retry, partition
- Consistency/coordination decision note

## Decision Checklist / Câu hỏi kiểm tra

- Node nào có thể fail độc lập?
- Message có thể duplicate, delay hoặc lost không?
- Data nào cần consistency guarantee nào?

## Failure Modes / Cách nó gây lỗi

- Assume network reliable
- Retry không kiểm soát gây duplicate/overload
- Service split làm transaction/debug khó hơn mà không có lợi ích

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu monolith/single DB đáp ứng tải và team
- Dễ over-engineer nếu phân tán trước khi có bottleneck/team boundary thật

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

## Keywords / Từ khóa tìm kiếm

- Distributed System
- distributed systems
- hệ phân tán
- distributed
- system
- Architecture
- System Design
- phân tán
- hệ thống
- kiến trúc hệ thống

## Source trace

- Designing Data-Intensive Applications Part II
