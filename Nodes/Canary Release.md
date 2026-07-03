# Canary Release

Aliases: canary deployment, phát hành canary

Type: Deployment / Operations

## Context / Ngữ cảnh

Canary Release xuất hiện khi version mới cần được thử trên một phần nhỏ traffic/user trước rollout rộng.

## Boundary / Ranh giới

### Nó là gì

Canary Release là progressive deployment đưa traffic tăng dần tới version mới dựa trên signal.

### Nó không phải là gì

Nó không thay thế test trước deploy và không hữu ích nếu không có monitoring tốt.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là route một phần traffic, so sánh metric/log/error, rồi continue hoặc rollback.

## Project Role / Vai trò trong dự án

Node này giảm blast radius cho thay đổi rủi ro cao.

## Output / Artifact nên có

- Canary cohort/percentage plan
- Promotion/rollback metric
- Duration và observation window

## Decision Checklist / Câu hỏi kiểm tra

- Canary traffic có đại diện user thật không?
- Metric nào đủ nhạy để stop rollout?
- Có automatic rollback hay manual decision?

## Failure Modes / Cách nó gây lỗi

- Sample quá nhỏ không phát hiện lỗi
- Canary không có metric nên chỉ là rollout chậm
- Canary user bị chọn sai gây bias

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu traffic quá thấp để canary có ý nghĩa
- Dễ over-engineer nếu deploy nhỏ hơn chi phí vận hành canary

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Deployment Strategy]] vì canary là progressive strategy
- [[Monitoring]] vì canary cần signal để quyết định

## Liên quan rộng

- Progressive delivery
- Blast radius

## Source trace

- Google SRE Books
- Continuous Delivery
