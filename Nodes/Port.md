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

- Listen/bind/expose port table
- Firewall/security-group rule
- Docker/load-balancer port mapping

## Decision Checklist / Câu hỏi kiểm tra

- Service listen ở port nào?
- Port đó bind localhost hay all interfaces?
- External mapping có trỏ đúng internal port không?

## Failure Modes / Cách nó gây lỗi

- App chạy nhưng bind localhost nên ngoài không vào
- Port conflict làm service không start
- Expose nhầm port admin ra public

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu platform quản lý endpoint hoàn toàn
- Dễ over-engineer nếu lỗi nằm ở DNS/API path chứ không ở port

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
