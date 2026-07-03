# Availability Zone

Aliases: AZ, vùng sẵn sàng, cloud availability zone

Type: Deployment / Operations

## Context / Ngữ cảnh

Availability Zone xuất hiện khi workload cần chịu lỗi datacenter trong cùng region.

## Boundary / Ranh giới

### Nó là gì

Availability Zone là failure domain riêng trong một cloud region.

### Nó không phải là gì

Nó không phải region khác và không tự bảo vệ nếu app không deploy đa AZ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là phân tán resource qua AZ để tránh single datacenter failure.

## Project Role / Vai trò trong dự án

Node này giúp thiết kế HA cho compute, load balancer và database.

## Output / Artifact nên có

- AZ placement map
- Multi-AZ failover assumption
- Cross-AZ cost/latency note

## Decision Checklist / Câu hỏi kiểm tra

- Resource có spread qua AZ không?
- Dependency quan trọng có cùng failure domain không?
- Failover giữa AZ đã test chưa?

## Failure Modes / Cách nó gây lỗi

- Tưởng multi-AZ nhưng DB vẫn single-AZ
- Cross-AZ traffic cost tăng bất ngờ
- AZ outage kéo cả stack vì dependency chung

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần multi-AZ cho prototype không SLA
- Dễ over-engineer nếu HA target thấp nhưng kiến trúc quá tốn cost

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Region]] vì AZ nằm trong region
- [[Fault Tolerance]] vì multi-AZ giảm blast radius

## Liên quan rộng

- Failure domain
- High availability

## Keywords / Từ khóa tìm kiếm

- Availability Zone
- AZ
- vùng sẵn sàng
- cloud availability zone
- availability
- zone
- Deployment
- Operations
- cloud infrastructure
- hạ tầng cloud

## Source trace

- AWS Well-Architected
- Google Cloud Architecture Framework
