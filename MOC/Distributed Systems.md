# Distributed Systems

Aliases: distributed computing, hệ phân tán

Type: Architecture / System Design

## Context / Ngữ cảnh

Distributed Systems là vùng kiến thức về hệ thống chạy trên nhiều node/process và phải sống chung với network, partial failure và consistency trade-off.

## Boundary / Ranh giới

### Nó là gì

Distributed Systems là MOC gom các node về coordination, replication, quorum, leader election, consistency và delivery guarantee.

### Nó không phải là gì

Nó không phải chỉ là microservices, không phải scaling miễn phí, và không nên dùng khi một hệ thống đơn giản đủ giải quyết vấn đề.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là phối hợp qua message/network trong khi từng node có thể chậm, mất kết nối hoặc fail độc lập.

## Project Role / Vai trò trong dự án

MOC này giúp đọc graph backend/data/SRE khi vấn đề vượt khỏi một process hoặc một database đơn lẻ.

## Output / Artifact nên có

- Distributed-system map: nodes, links, failure domains
- Consistency/failure assumptions
- Coordination or messaging decision note

## Decision Checklist / Câu hỏi kiểm tra

- Có thật sự cần nhiều node/process không?
- Partial failure nào phải chịu được?
- Consistency/availability trade-off nằm ở dữ liệu nào?

## Failure Modes / Cách nó gây lỗi

- Thiết kế như local call nên không chịu timeout/retry
- Không ghi failure domain nên redundancy giả
- Bỏ qua network partition rồi debug production rất muộn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu một process/database đủ giải quyết vấn đề
- Dễ over-engineer nếu tách service chỉ để graph nhìn hiện đại

## Gồm những gì

- [[Distributed System]]
- [[Fault Tolerance]]
- [[Leader Election]]
- [[Quorum]]
- [[CAP Theorem]]
- [[Exactly Once]]
- [[At Least Once]]
- [[Split Brain]]
- [[Circuit Breaker]]
- [[Retry]]
- [[Exponential Backoff]]

## Nối mạnh


- Chưa có nối mạnh ngoài các node con trực tiếp
## Liên quan rộng

- Data Intensive Systems vì distributed data là một nhánh lớn của data-intensive systems
- SRE and Reliability vì vận hành distributed systems cần reliability discipline
- Coordination
- Partial failure
- Replication
- Message delivery

## Keywords / Từ khóa tìm kiếm

- Distributed Systems
- Distributed Systems MOC
- distributed systems map
- mục lục kiến thức
- nhánh kiến thức
- distributed computing
- hệ phân tán
- architecture decision
- system boundary
- component responsibility
- kiến trúc hệ thống
- ranh giới hệ thống
- Distributed System
- Fault Tolerance
- Leader Election

## Source trace

- Designing Data-Intensive Applications
- MIT distributed systems notes
- Google SRE Books
