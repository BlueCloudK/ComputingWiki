# Public Subnet

Aliases: Public Subnet, internet-facing subnet

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Public Subnet xuất hiện trong cloud network khi resource trong subnet cần có đường route ra/vào internet thông qua internet gateway, load balancer hoặc public IP.

## Boundary / Ranh giới

### Nó là gì

Public Subnet là subnet có route tới internet gateway và có thể chứa resource internet-facing như load balancer, bastion host hoặc NAT gateway tùy cloud design.

### Nó không phải là gì

Public Subnet không tự động làm mọi resource public. Security group, firewall, public IP, route table và service binding vẫn quyết định traffic thật có vào được hay không.

## Core Mechanism / Cơ chế lõi

Subnet gắn với route table có default route ra internet gateway. Resource muốn nhận traffic trực tiếp thường cần public IP hoặc load balancer mapping, đồng thời network ACL/security group cho phép port/protocol phù hợp.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế VPC/VNet, expose load balancer, đặt NAT/bastion, debug service không truy cập được từ internet hoặc tách public/private tier.

## Output / Artifact nên có

- Subnet CIDR
- Route table
- Internet gateway mapping
- Security group/firewall rule
- Public/private placement decision

## Decision Checklist / Câu hỏi kiểm tra

- Subnet có default route ra internet gateway không?
- Resource có public IP hoặc load balancer không?
- Firewall/security group mở đúng port chưa?
- Resource này có thật sự nên nằm public subnet không?
- Private subnet có cần NAT để outbound không?

## Failure Modes / Cách nó gây lỗi

- Route public nhưng security group chặn nên không vào được.
- Resource nhạy cảm bị đặt public subnet không cần thiết.
- Public IP mở rộng làm tăng attack surface.
- Load balancer public nhưng backend/private route sai.
- Nhầm public subnet với private subnet có outbound NAT.

## Khi nào chưa cần hoặc dễ over-engineer

- Service nội bộ không cần internet-facing path thì nên ở private subnet.
- Không nên đưa database/stateful service ra public subnet nếu có thể đặt sau private boundary.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Least Privilege]] vì public exposure cần scope nhỏ nhất có thể.
- [[Load Balancer]] vì public traffic thường đi qua load balancer.
- [[API Gateway]] vì API public có thể nằm trước private backend.
- [[TLS]] vì public endpoint cần transport security.

## Liên quan rộng

- VPC networking
- Route table
- Internet gateway
- Public IP

## Keywords / Từ khóa tìm kiếm

- Public Subnet
- internet-facing subnet
- route table
- internet gateway
- public IP
- security group
- public subnet debugging

## Source trace

- AWS VPC documentation
- Google Cloud VPC documentation
