# VPC

Aliases: Virtual Private Cloud, mạng riêng ảo cloud

Type: Deployment / Operations

## Context / Ngữ cảnh

VPC xuất hiện khi cloud resource cần network boundary riêng, subnet, routing và security rule.

## Boundary / Ranh giới

### Nó là gì

VPC là private network abstraction trong cloud để cô lập và kết nối resource.

### Nó không phải là gì

Nó không phải VPN và không tự bảo mật nếu route/security group mở sai.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là CIDR, subnet, route table, gateway, firewall/security group và peering.

## Project Role / Vai trò trong dự án

Node này giúp debug connectivity, exposure và blast radius của cloud workload.

## Output / Artifact nên có

- VPC/subnet/route diagram
- Security group/firewall policy
- Public/private boundary note

## Decision Checklist / Câu hỏi kiểm tra

- Resource nào cần public subnet?
- Route table/gateway có đúng outbound/inbound không?
- CIDR có overlap với peering/VPN không?

## Failure Modes / Cách nó gây lỗi

- DB nằm public subnet
- CIDR overlap làm peering lỗi
- Security group mở rộng quá mức

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần VPC design sâu nếu dùng managed platform đơn giản
- Dễ over-engineer nếu network segmentation vượt nhu cầu bảo mật/vận hành

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Cloud Computing]] vì VPC là network primitive cloud
- [[Network Security]] vì VPC boundary ảnh hưởng exposure

## Liên quan rộng

- Subnets
- Cloud networking

## Source trace

- AWS Well-Architected
- Google Cloud Architecture Framework
