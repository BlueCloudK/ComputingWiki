# Terraform Plan

Aliases: Terraform Plan, terraform plan

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Terraform Plan xuất hiện khi cần xem trước infrastructure change trước khi apply lên cloud/provider thật.

## Boundary / Ranh giới

### Nó là gì

Terraform Plan là bước Terraform so sánh config, state và provider reality để tạo danh sách resource sẽ create, update, replace hoặc destroy.

### Nó không phải là gì

Terraform Plan không phải đảm bảo tuyệt đối apply sẽ thành công. State có thể đổi sau plan, provider có thể lỗi, permission có thể thiếu hoặc plan có thể bị stale.

## Core Mechanism / Cơ chế lõi

Terraform đọc configuration, refresh hoặc đọc state, tính dependency graph và tạo execution plan. Plan cho biết action dự kiến, attribute thay đổi và resource nào có thể bị recreate/destroy.

## Project Role / Vai trò trong dự án

Dùng node này khi review IaC PR, kiểm tra drift, tránh destroy nhầm resource, chuẩn bị approval trước apply hoặc debug vì sao Terraform muốn thay đổi resource ngoài ý muốn.

## Output / Artifact nên có

- Plan output hoặc saved plan file
- Resource action summary
- Destroy/replace warning
- Workspace/environment context
- Reviewer approval note nếu production

## Decision Checklist / Câu hỏi kiểm tra

- Plan chạy ở workspace/environment nào?
- Có resource destroy/replace không?
- Change có đúng với intent PR không?
- State có mới và không drift không?
- Apply có dùng đúng plan đã review không?

## Failure Modes / Cách nó gây lỗi

- Reviewer bỏ sót `destroy` hoặc `replace`.
- Plan chạy nhầm workspace.
- Plan stale vì state/reality đổi trước apply.
- Sensitive value lộ trong plan/log.
- Plan pass nhưng provider permission thiếu lúc apply.

## Khi nào chưa cần hoặc dễ over-engineer

- Lab nhỏ có thể plan/apply local, nhưng production nên tách plan review rõ.
- Không nên auto-approve plan nếu chưa có policy check và owner rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Terraform Apply]] vì plan là input/review trước khi apply.
- [[Terraform Provider]] vì provider quyết định resource diff và API behavior.
- [[State Locking]] vì state cần được bảo vệ khi plan/apply.
- [[Config Drift]] vì plan thường lộ drift giữa config và reality.

## Liên quan rộng

- Infrastructure as Code
- Plan review
- Cloud provisioning

## Keywords / Từ khóa tìm kiếm

- Terraform Plan
- terraform plan
- infrastructure plan
- resource diff
- Terraform destroy
- Terraform replace
- terraform plan debugging

## Source trace

- Terraform documentation
