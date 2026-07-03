# Port

Aliases: network port, cổng mạng

Type: Tooling / Implementation Detail

## Context / Ngữ cảnh

Port xuất hiện khi OS/network cần phân biệt process/service trên cùng host/IP.

## Boundary / Ranh giới

### Nó là gì

Port là số ở transport layer để demultiplex connection/datagram tới process.

### Nó không phải là gì

Nó không phải physical port hay permission role.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là bind/connect theo address, protocol và port number.

## Project Role / Vai trò trong dự án

Node này giúp debug service binding, firewall, Docker port mapping và API endpoint.

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

- [[TCP]] vì TCP connection dùng port
- [[UDP]] vì UDP datagram dùng port
- [[Socket]] vì socket bind/connect theo address-port

## Liên quan rộng

- Service discovery
- Firewall rules

## Source trace

- Computer Networks Map
