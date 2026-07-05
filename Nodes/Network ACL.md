# Network ACL

Aliases: Network ACL, network access control list

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Network ACL xuất hiện trong cloud network khi subnet hoặc network boundary cần rule allow/deny traffic ở tầng IP/port/protocol.

## Boundary / Ranh giới

### Nó là gì

Network ACL là rule set kiểm soát traffic vào/ra ở network/subnet boundary, thường stateless hoặc gần stateless tùy platform.

### Nó không phải là gì

Network ACL không giống security group/application auth. ACL xử lý network packet boundary; app-level authorization vẫn phải nằm ở tầng service/app.

## Core Mechanism / Cơ chế lõi

Traffic được so với rule theo thứ tự/priority. Rule match source/destination CIDR, port, protocol và action allow/deny. Với ACL stateless, inbound và outbound/ephemeral port cần được cho phép riêng.

## Project Role / Vai trò trong dự án

Dùng node này khi debug service không kết nối được, subnet public/private, network segmentation, blast radius hoặc policy deny ở tầng cloud network.

## Output / Artifact nên có

- ACL rule list
- Subnet/network attachment
- Source/destination CIDR
- Port/protocol matrix
- Test path: client → subnet → service

## Decision Checklist / Câu hỏi kiểm tra

- Rule áp ở subnet/network nào?
- Inbound và outbound đều được phép chưa?
- Ephemeral port có bị chặn không?
- Rule priority/order có match đúng không?
- ACL có overlap/conflict với security group/firewall không?

## Failure Modes / Cách nó gây lỗi

- Chỉ mở inbound nhưng outbound response bị chặn.
- Deny rule priority cao hơn allow rule mong muốn.
- CIDR quá rộng làm tăng attack surface.
- CIDR quá hẹp làm traffic hợp lệ bị block.
- Nhầm lỗi ACL với lỗi app/TLS/DNS.

## Khi nào chưa cần hoặc dễ over-engineer

- Network nhỏ có security group/firewall đủ rõ có thể chưa cần ACL phức tạp.
- Không nên dùng ACL làm lớp authorization nghiệp vụ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Network Segmentation]] vì ACL là công cụ chia boundary network.
- [[Public Subnet]] vì subnet public thường cần ACL/firewall rõ.
- [[Least Privilege]] vì rule nên mở phạm vi nhỏ nhất cần thiết.
- [[Security Group]] vì ACL và security group cùng ảnh hưởng traffic path.

## Liên quan rộng

- Subnet firewall
- CIDR rule
- Cloud networking

## Keywords / Từ khóa tìm kiếm

- Network ACL
- network access control list
- subnet ACL
- inbound outbound rule
- ephemeral port
- CIDR allow deny
- network ACL debugging

## Source trace

- AWS VPC documentation
- Google Cloud VPC documentation
