# DHCP

Aliases: Dynamic Host Configuration Protocol, DHCP

Type: Protocol / Data Format

## Context / Ngữ cảnh

DHCP xuất hiện khi device cần nhận IP config tự động trong network.

## Boundary / Ranh giới

### Nó là gì

DHCP là protocol cấp IP, gateway, DNS và lease cho client.

### Nó không phải là gì

Nó không phải DNS hay routing protocol.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là discover/offer/request/ack giữa client và DHCP server.

## Project Role / Vai trò trong dự án

Node này giúp debug máy không vào mạng, IP conflict hoặc network lab.

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

- [[IP]] vì DHCP cấp IP config
- [[DNS]] vì DHCP thường cấp DNS server

## Liên quan rộng

- Network configuration

## Source trace

- Computer Networks Map
