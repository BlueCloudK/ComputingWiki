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

- [[Distributed System]]
- [[Fault Tolerance]]
- [[Leader Election]]
- [[Quorum]]
- [[CAP Theorem]]
- [[Exactly Once]]
- [[At Least Once]]

## Nối mạnh

- [[Data Intensive Systems]] vì distributed data là một nhánh lớn của data-intensive systems
- [[SRE and Reliability]] vì vận hành distributed systems cần reliability discipline

## Liên quan rộng

- Coordination
- Partial failure
- Replication
- Message delivery

## Source trace

- Designing Data-Intensive Applications
- MIT distributed systems notes
- Google SRE Books
