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

- Packet capture filter hoặc trace
- Header/path note: source, dest, protocol, size
- Loss/reorder/fragment evidence

## Decision Checklist / Câu hỏi kiểm tra

- Packet có rời host nguồn không?
- MTU/fragmentation có liên quan không?
- Drop xảy ra ở firewall/router hay app?

## Failure Modes / Cách nó gây lỗi

- Nhầm API error với packet loss
- MTU black hole làm request lớn fail
- Capture sai interface nên kết luận nhầm

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần packet-level debug khi app logs đủ
- Dễ over-engineer nếu đọc packet trước khi hiểu request flow

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[IP]] vì IP truyền packet/datagram
- [[TCP]] vì TCP xây stream tin cậy trên packet network

## Liên quan rộng

- Network troubleshooting

## Source trace

- Computer Networks Map
