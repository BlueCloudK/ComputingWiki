# Remote State

Aliases: Remote State, Terraform remote state

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Remote State xuất hiện trong Infrastructure as Code khi nhiều người hoặc pipeline cần dùng chung state của Terraform/OpenTofu thay vì giữ state file local trên một máy.

## Boundary / Ranh giới

### Nó là gì

Remote State là state file được lưu ở backend dùng chung như object storage, Terraform Cloud hoặc state service, thường kèm locking và access control.

### Nó không phải là gì

Remote State không phải source code IaC. Config mô tả desired state; remote state ghi mapping giữa config và resource thật đã được tạo.

## Core Mechanism / Cơ chế lõi

Terraform đọc state từ backend, lock state khi plan/apply nếu backend hỗ trợ, cập nhật state sau apply và dùng state để biết resource nào đang được quản lý.

## Project Role / Vai trò trong dự án

Dùng node này khi setup Terraform team workflow, debug state drift, state lock, pipeline apply song song, backend permission hoặc migrate state local lên remote.

## Output / Artifact nên có

- Backend config
- State bucket/workspace path
- Locking mechanism
- Access policy
- Backup/versioning rule

## Decision Checklist / Câu hỏi kiểm tra

- State backend nằm ở đâu?
- State có locking không?
- Ai/pipeline nào được đọc/ghi state?
- State có chứa sensitive output không?
- Backend có versioning/backup không?

## Failure Modes / Cách nó gây lỗi

- Hai apply song song làm state conflict nếu thiếu lock.
- State bị mất hoặc overwrite làm Terraform muốn recreate resource.
- State chứa secret/output nhạy cảm nhưng access quá rộng.
- Backend permission sai làm pipeline plan/apply fail.
- Migrate state sai workspace làm resource bị orphan hoặc duplicate.

## Khi nào chưa cần hoặc dễ over-engineer

- Lab một người có thể bắt đầu local state, nhưng production/team nên dùng remote state sớm.
- Không nên xem remote state là backup duy nhất cho hạ tầng thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Terraform Plan]] vì plan dùng state để tính diff.
- [[Terraform Apply]] vì apply cập nhật state sau khi đổi resource.
- [[State Locking]] vì remote state cần lock để tránh apply song song.
- [[Pipeline Secret]] vì backend credential thường được inject vào CI/CD.

## Liên quan rộng

- IaC backend
- State file
- Terraform workspace

## Keywords / Từ khóa tìm kiếm

- Remote State
- Terraform remote state
- state backend
- state lock
- Terraform workspace
- remote state backend
- remote state debugging

## Source trace

- Terraform documentation
- OpenTofu documentation
