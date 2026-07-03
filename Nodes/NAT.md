# NAT

Aliases: Network Address Translation, dịch địa chỉ mạng

Type: Tooling / Implementation Detail

## Context / Ngữ cảnh

NAT xuất hiện khi nhiều host private cần dùng public IP hoặc network boundary cần translate address/port.

## Boundary / Ranh giới

### Nó là gì

NAT là cơ chế rewrite IP/port giữa hai network boundary.

### Nó không phải là gì

Nó không phải firewall đầy đủ hoặc DNS.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là giữ translation table và rewrite packet address/port khi đi qua boundary.

## Project Role / Vai trò trong dự án

Node này giúp debug connectivity, inbound service, Docker/cloud networking và peer-to-peer issues.

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

- [[IP]] vì NAT rewrite IP addressing
- [[Port]] vì NAT thường translate port mapping

## Liên quan rộng

- Private networks
- Port forwarding

## Source trace

- Computer Networks Map
