# Infrastructure Drift

Aliases: Infrastructure Drift, infrastructure drift

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Infrastructure Drift xuất hiện trong cloud devops tooling là vùng kiến thức về iac, ci/cd, gitops, observability, artifact, runtime platform và vận hành cloud.

## Boundary / Ranh giới

### Nó là gì

Infrastructure Drift là khái niệm giúp đặt tên đúng một phần của hệ thống, workflow hoặc failure mode trong vùng Cloud / DevOps Tooling.

### Nó không phải là gì

Nó không phải keyword để nhồi vào graph; node này chỉ hữu ích khi nối được với artifact, decision hoặc debug path cụ thể.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Infrastructure Drift nằm ở boundary nào, input/output là gì, state hoặc config nào liên quan, và lỗi thường lộ ra bằng signal nào.

## Project Role / Vai trò trong dự án

Infrastructure Drift giúp team thiết kế, review, test, deploy hoặc vận hành hệ thống bằng cùng một ngôn ngữ thay vì chỉ dựa vào tool cụ thể.

## Output / Artifact nên có

- Decision note hoặc config liên quan tới Infrastructure Drift
- Test/checklist/metric nếu concept nằm trên critical path
- Runbook hoặc debug note nếu có impact production

## Decision Checklist / Câu hỏi kiểm tra

- Infrastructure Drift giải quyết constraint cụ thể nào?
- Owner, boundary và rollback path có rõ không?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng Infrastructure Drift sai boundary làm debug hoặc design lệch hướng
- Thiếu metric/test khiến lỗi chỉ lộ khi scale, deploy hoặc tích hợp thật
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Infrastructure Drift nếu hệ thống nhỏ và chưa chạm constraint liên quan
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Cloud and Infrastructure
- Deployment and Operations
- Linux and Server Admin
- SRE and Reliability

## Keywords / Từ khóa tìm kiếm

- Infrastructure Drift
- infrastructure drift
- infrastructure drift design
- infrastructure drift debugging
- infrastructure drift production
- infrastructure drift best practice

## Source trace

- Kubernetes official docs
- OpenTelemetry documentation
- Terraform documentation
- GitHub Actions documentation
