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

- Terraform module/config
- Plan output review
- State backend/locking policy
- Workspace/environment mapping

## Decision Checklist / Câu hỏi kiểm tra

- State lưu ở đâu và có lock không?
- Plan có destroy/replace bất ngờ không?
- Provider/module version có pin không?

## Failure Modes / Cách nó gây lỗi

- Apply nhầm workspace phá production
- State file leak secret
- Drift do sửa console ngoài Terraform

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Terraform cho resource tạm rất ít
- Dễ over-engineer nếu module abstraction phức tạp hơn hạ tầng thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Infrastructure as Code]] vì Terraform là IaC tool phổ biến
- [[Cloud Computing]] vì Terraform hay quản lý cloud resource

## Liên quan rộng

- IaC workflow
- State management

## Keywords / Từ khóa tìm kiếm

- Terraform
- Terraform IaC
- Deployment
- Operations
- cloud infrastructure
- hạ tầng cloud
- devops
- triển khai phần mềm

## Source trace

- Terraform official docs
