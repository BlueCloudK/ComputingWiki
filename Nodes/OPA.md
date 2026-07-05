# OPA

Aliases: OPA, Open Policy Agent

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

OPA xuất hiện khi hệ thống cần policy-as-code để kiểm soát admission, authorization, CI policy, infrastructure rule hoặc compliance check.

## Boundary / Ranh giới

### Nó là gì

OPA là policy engine dùng để đánh giá input data theo policy viết bằng Rego và trả decision như allow/deny/violation.

### Nó không phải là gì

OPA không phải IAM hoàn chỉnh tự thân. Nó là engine ra quyết định policy; hệ thống gọi OPA vẫn phải enforce quyết định đó đúng chỗ.

## Core Mechanism / Cơ chế lõi

Ứng dụng, Kubernetes admission controller hoặc CI gửi input JSON cho OPA. OPA evaluate policy bundle và trả decision. Policy có thể được test, version và deploy như code.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế guardrail cho Kubernetes, Terraform, CI/CD, API authorization hoặc agent/tool approval policy.

## Output / Artifact nên có

- Rego policy
- Input schema/sample
- Decision contract
- Policy test cases
- Enforcement point mapping

## Decision Checklist / Câu hỏi kiểm tra

- Policy được enforce ở đâu?
- Input data có đủ field để quyết định không?
- Decision allow/deny/violation có contract rõ không?
- Policy có test case positive/negative không?
- Nếu OPA lỗi thì hệ thống fail open hay fail closed?

## Failure Modes / Cách nó gây lỗi

- Policy đúng nhưng không được enforce thật.
- Input thiếu field làm decision sai.
- Rule quá rộng deny nhầm workload hợp lệ.
- Không test policy nên change nhỏ phá production.
- Fail-open làm guardrail mất tác dụng khi OPA lỗi.

## Khi nào chưa cần hoặc dễ over-engineer

- Hệ thống nhỏ có vài rule có thể dùng validation/config guard đơn giản trước.
- Không nên thêm OPA nếu chưa xác định enforcement point và owner policy.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authorization]] vì OPA thường dùng để ra quyết định allow/deny.
- [[Kubernetes RBAC]] vì OPA bổ sung policy cho admission/cluster control.
- [[Least Privilege]] vì policy-as-code giúp enforce quyền tối thiểu.
- [[Deployment Approval]] vì policy decision có thể là gate trước deploy.

## Liên quan rộng

- Policy as code
- Admission control
- Compliance guardrail

## Keywords / Từ khóa tìm kiếm

- OPA
- Open Policy Agent
- Rego
- policy as code
- admission control
- authorization policy
- OPA debugging

## Source trace

- Open Policy Agent documentation
- Kubernetes official docs
