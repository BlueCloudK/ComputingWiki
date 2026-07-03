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

- [[Deployment Strategy]] vì canary là progressive strategy
- [[Monitoring]] vì canary cần signal để quyết định

## Liên quan rộng

- Progressive delivery
- Blast radius

## Source trace

- Google SRE Books
- Continuous Delivery
