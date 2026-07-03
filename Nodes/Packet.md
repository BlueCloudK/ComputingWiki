# Packet

Aliases: network packet, gói tin

Type: Protocol / Data Format

## Context / Ngữ cảnh

Packet xuất hiện khi dữ liệu network được chia thành đơn vị truyền qua layer thấp.

## Boundary / Ranh giới

### Nó là gì

Packet là đơn vị dữ liệu gồm header và payload đi qua network.

### Nó không phải là gì

Nó không phải API request nguyên vẹn.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là encapsulation, forwarding và có thể drop/reorder/fragment tùy layer.

## Project Role / Vai trò trong dự án

Node này giúp debug latency, loss, MTU và protocol behavior.

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

- [[IP]] vì IP truyền packet/datagram
- [[TCP]] vì TCP xây stream tin cậy trên packet network

## Liên quan rộng

- Network troubleshooting

## Source trace

- Computer Networks Map
