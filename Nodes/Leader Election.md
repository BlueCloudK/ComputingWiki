# Leader Election

Aliases: leader election, bầu leader

Type: Data / Database

## Context / Ngữ cảnh

Leader Election xuất hiện khi cluster cần chọn một node làm coordinator hoặc primary để tránh split decision.

## Boundary / Ranh giới

### Nó là gì

Leader Election là protocol/chọn lựa để xác định node leader trong nhóm distributed nodes.

### Nó không phải là gì

Nó không phải human team leadership và không thay thế consensus đầy đủ trong mọi trường hợp.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là heartbeat, term, vote hoặc lease để chọn leader và phát hiện leader fail.

## Project Role / Vai trò trong dự án

Node này giúp hiểu failover, primary replica, scheduler và distributed coordination.

## Output / Artifact nên có

- Leader election rule: term, vote, lease hoặc heartbeat
- Failover timeout và split-brain protection
- Operational note cho leader change

## Decision Checklist / Câu hỏi kiểm tra

- Leader chết thì phát hiện sau bao lâu?
- Có thể có hai leader cùng lúc không?
- Client/replica biết leader mới thế nào?

## Failure Modes / Cách nó gây lỗi

- Split brain làm ghi dữ liệu mâu thuẫn
- Lease quá dài làm failover chậm
- Clock/heartbeat assumption sai gây election loop

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không có cluster/primary replica
- Dễ over-engineer nếu một scheduler/process duy nhất đủ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Consensus]] vì election thường dựa vào consensus/coordination
- [[Fault Tolerance]] vì leader fail phải được xử lý

## Liên quan rộng

- Cluster coordination

## Keywords / Từ khóa tìm kiếm

- Leader Election
- distributed leader
- consensus leader
- primary node election
- split brain prevention
- bầu chọn leader

## Source trace

- DDIA Ch09
