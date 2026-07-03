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

- Lease/config record: IP, gateway, DNS
- DHCP scope/reservation note
- Troubleshooting note cho client không nhận IP

## Decision Checklist / Câu hỏi kiểm tra

- Client có nhận lease hợp lệ không?
- Gateway/DNS từ DHCP có đúng network không?
- Lease conflict hoặc scope exhaustion có xảy ra không?

## Failure Modes / Cách nó gây lỗi

- Scope hết IP làm máy không vào mạng
- Gateway/DNS sai khiến app tưởng service down
- IP conflict do reservation lỗi

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu dùng static config đơn giản
- Dễ over-engineer nếu app-level issue không liên quan network config

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[IP]] vì DHCP cấp IP config
- [[DNS]] vì DHCP thường cấp DNS server

## Liên quan rộng

- Network configuration

## Source trace

- Computer Networks Map
