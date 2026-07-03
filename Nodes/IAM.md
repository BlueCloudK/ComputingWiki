# IAM

Aliases: Identity and Access Management, quản lý định danh và quyền

Type: Security

## Context / Ngữ cảnh

IAM xuất hiện khi cloud/service cần quản lý ai hoặc workload nào được làm gì trên resource nào.

## Boundary / Ranh giới

### Nó là gì

IAM là hệ thống identity, role, policy và permission cho người dùng hoặc service.

### Nó không phải là gì

Nó không phải authentication app end-user và không thay thế least privilege review.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là principal + action + resource + condition quyết định allow/deny.

## Project Role / Vai trò trong dự án

Node này là trung tâm bảo vệ cloud resource, CI/CD secret và service-to-service access.

## Output / Artifact nên có

- Principal/action/resource policy table
- Role assumption/rotation rule
- Access review evidence

## Decision Checklist / Câu hỏi kiểm tra

- Principal này cần action cụ thể nào?
- Policy có wildcard nguy hiểm không?
- Credential ngắn hạn hay long-lived key?

## Failure Modes / Cách nó gây lỗi

- Admin role dùng cho CI/service
- Key leak trong log/repo
- Policy chồng chéo không audit được

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần IAM phức tạp cho local-only prototype
- Dễ over-engineer nếu permission quá nhỏ làm delivery nghẹt mà không giảm blast radius

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Least Privilege]] vì IAM policy nên tối thiểu quyền
- [[Secret]] vì credential/IAM key cần bảo vệ

## Liên quan rộng

- Cloud security
- Service accounts

## Source trace

- AWS Well-Architected Security Pillar
- Google Cloud IAM docs
