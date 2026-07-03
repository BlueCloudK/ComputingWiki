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

- Listener/routing rule
- Health check/readiness config
- TLS termination và backend pool note

## Decision Checklist / Câu hỏi kiểm tra

- Health check có phản ánh readiness thật không?
- Traffic routing theo host/path/header nào?
- Backend unhealthy xử lý ra sao?

## Failure Modes / Cách nó gây lỗi

- Health check xanh giả làm LB gửi traffic vào instance lỗi
- Sticky session gây lệch tải
- TLS/proxy header sai làm app redirect loop

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần LB nếu một instance nội bộ là đủ
- Dễ over-engineer nếu LB che bug readiness/deploy thay vì sửa app

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
