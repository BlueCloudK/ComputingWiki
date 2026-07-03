# Load Balancer

Aliases: LB, cân bằng tải

Type: Deployment / Operations

## Context / Ngữ cảnh

Load Balancer xuất hiện khi nhiều instance/service cần nhận traffic theo rule ổn định.

## Boundary / Ranh giới

### Nó là gì

Load Balancer phân phối request hoặc connection tới backend lành mạnh.

### Nó không phải là gì

Nó không sửa app chậm và không thay thế autoscaling/health check tốt.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là health check, routing, balancing algorithm và optional TLS termination.

## Project Role / Vai trò trong dự án

Node này giúp scale, HA và deploy nhiều instance an toàn hơn.

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

- [[Cloud Computing]] vì load balancer là managed resource phổ biến
- [[Deployment Strategy]] vì rollout thường điều khiển traffic qua LB

## Liên quan rộng

- Traffic routing
- High availability

## Source trace

- AWS Well-Architected
- Cloud architecture docs
