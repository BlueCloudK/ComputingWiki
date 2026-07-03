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

- NAT mapping/port-forward rule
- Private/public address boundary diagram
- Connection tracking note khi debug

## Decision Checklist / Câu hỏi kiểm tra

- Traffic outbound hay inbound qua NAT?
- Port mapping có đúng protocol và destination không?
- Timeout mapping có phá long-lived connection không?

## Failure Modes / Cách nó gây lỗi

- Service private không reachable vì thiếu port forward
- Hairpin NAT/Docker mapping gây nhầm endpoint
- NAT timeout làm connection rớt

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không debug network boundary
- Dễ over-engineer nếu DNS/firewall mới là nguyên nhân

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[IP]] vì NAT rewrite IP addressing
- [[Port]] vì NAT thường translate port mapping

## Liên quan rộng

- Private networks
- Port forwarding

## Keywords / Từ khóa tìm kiếm

- NAT
- Network Address Translation
- private IP translation
- public IP sharing
- port forwarding
- NAT gateway
- dịch địa chỉ mạng

## Source trace

- Computer Networks Map
