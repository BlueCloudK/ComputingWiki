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

- Chưa tách nhánh

## Nối mạnh

- [[Consensus]] vì election thường dựa vào consensus/coordination
- [[Fault Tolerance]] vì leader fail phải được xử lý

## Liên quan rộng

- Cluster coordination

## Source trace

- DDIA Ch09
