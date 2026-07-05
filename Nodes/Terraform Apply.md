# Terraform Apply

Aliases: Terraform Apply, terraform apply

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Terraform Apply xuất hiện khi IaC change đã được plan/review và cần thực thi để tạo, sửa hoặc xóa resource thật trên cloud/platform.

## Boundary / Ranh giới

### Nó là gì

Terraform Apply là lệnh/step thực thi Terraform plan lên provider API, cập nhật infrastructure thực tế và state file theo thay đổi đã tính.

### Nó không phải là gì

Terraform Apply không phải bước thử vô hại. Apply có thể thay đổi production resource, xóa dữ liệu hoặc gây downtime nếu plan/approval/state không được kiểm soát.

## Core Mechanism / Cơ chế lõi

Terraform đọc config, state và provider, tạo execution plan rồi apply plan bằng API call tới provider. Sau khi action thành công, Terraform cập nhật state để phản ánh resource hiện tại.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế IaC pipeline, review infra change, debug apply fail, state lock, drift hoặc production approval cho infrastructure.

## Output / Artifact nên có

- Terraform plan đã review
- Apply log
- State update
- Approval/audit record nếu production
- Rollback/remediation note

## Decision Checklist / Câu hỏi kiểm tra

- Plan có được review chưa?
- Apply chạy ở workspace/environment nào?
- State lock có hoạt động không?
- Change có destroy/recreate resource nhạy cảm không?
- Nếu apply fail giữa chừng thì xử lý ra sao?

## Failure Modes / Cách nó gây lỗi

- Apply nhầm workspace/environment.
- Plan có destroy resource nhưng reviewer bỏ sót.
- State lock thiếu làm hai apply chạy song song.
- Apply fail giữa chừng khiến state/thực tế lệch.
- Provider credential quá rộng làm blast radius lớn.

## Khi nào chưa cần hoặc dễ over-engineer

- Infra thử nghiệm nhỏ có thể apply local, nhưng production nên có plan/review/approval.
- Không nên auto-apply production nếu chưa có guardrail, state backend và rollback path rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Terraform Provider]] vì apply gọi provider API để đổi resource.
- [[Deployment Approval]] vì production apply thường cần approval gate.
- [[Pipeline Secret]] vì apply cần credential provider trong CI.
- [[Config Drift]] vì apply/state liên quan drift giữa config và reality.

## Liên quan rộng

- Infrastructure as Code
- Terraform state
- Cloud provisioning

## Keywords / Từ khóa tìm kiếm

- Terraform Apply
- terraform apply
- Terraform plan
- state lock
- workspace
- infrastructure change
- terraform apply debugging

## Source trace

- Terraform documentation
