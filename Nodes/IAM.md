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

- [[Least Privilege]] vì IAM policy nên tối thiểu quyền
- [[Secret]] vì credential/IAM key cần bảo vệ

## Liên quan rộng

- Cloud security
- Service accounts

## Source trace

- AWS Well-Architected Security Pillar
- Google Cloud IAM docs
