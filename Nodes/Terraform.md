# Terraform

Aliases: Terraform, Terraform IaC

Type: Deployment / Operations

## Context / Ngữ cảnh

Terraform xuất hiện khi infrastructure cần được mô tả bằng declarative config và apply qua provider.

## Boundary / Ranh giới

### Nó là gì

Terraform là IaC tool quản lý resource bằng configuration, provider và state.

### Nó không phải là gì

Nó không phải cloud provider, không tự thiết kế architecture tốt, và state cần bảo vệ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là plan/apply: so desired config với state/remote rồi tạo update/delete resource.

## Project Role / Vai trò trong dự án

Node này giúp quản lý cloud resource có review, history và drift awareness.

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

- [[Infrastructure as Code]] vì Terraform là IaC tool phổ biến
- [[Cloud Computing]] vì Terraform hay quản lý cloud resource

## Liên quan rộng

- IaC workflow
- State management

## Source trace

- Terraform official docs
