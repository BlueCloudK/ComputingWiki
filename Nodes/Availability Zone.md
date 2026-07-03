# Availability Zone

Aliases: AZ, vùng sẵn sàng

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

- [[Region]] vì AZ nằm trong region
- [[Fault Tolerance]] vì multi-AZ giảm blast radius

## Liên quan rộng

- Failure domain
- High availability

## Source trace

- AWS Well-Architected
- Google Cloud Architecture Framework
