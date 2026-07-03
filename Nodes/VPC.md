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

- [[Cloud Computing]] vì VPC là network primitive cloud
- [[Network Security]] vì VPC boundary ảnh hưởng exposure

## Liên quan rộng

- Subnets
- Cloud networking

## Source trace

- AWS Well-Architected
- Google Cloud Architecture Framework
