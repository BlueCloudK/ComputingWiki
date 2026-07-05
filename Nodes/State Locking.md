# State Locking

Aliases: State Locking, Terraform state locking

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

State Locking xuất hiện trong Infrastructure as Code khi nhiều người hoặc pipeline có thể plan/apply cùng một remote state và cần tránh ghi state song song.

## Boundary / Ranh giới

### Nó là gì

State Locking là cơ chế khóa state file/backend trong lúc plan/apply/migrate để chỉ một writer được thay đổi state tại một thời điểm.

### Nó không phải là gì

State Locking không giải quyết mọi drift hoặc mọi conflict hạ tầng. Nó chỉ bảo vệ state khỏi concurrent write; vẫn cần review plan, access control và drift detection.

## Core Mechanism / Cơ chế lõi

Khi Terraform/OpenTofu bắt đầu operation cần ghi state, backend tạo lock. Operation khác thấy lock sẽ chờ hoặc fail. Khi apply xong hoặc process giải phóng lock, backend unlock để operation tiếp theo chạy.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Terraform apply bị kẹt, force-unlock, pipeline chạy song song, remote state conflict hoặc state corruption risk.

## Output / Artifact nên có

- Lock backend/mechanism
- Lock owner/run ID
- Timeout/wait behavior
- Force-unlock procedure
- Audit trail for state writes

## Decision Checklist / Câu hỏi kiểm tra

- Backend có hỗ trợ locking không?
- Ai đang giữ lock và từ run nào?
- Lock còn sống thật hay stale?
- Có pipeline nào chạy apply song song không?
- Force-unlock có an toàn ở thời điểm này không?

## Failure Modes / Cách nó gây lỗi

- Không có locking làm hai apply ghi state đè nhau.
- Lock stale làm pipeline kẹt.
- Force-unlock khi apply vẫn đang chạy làm state corrupt.
- State backend permission sai làm lock không tạo được.
- Plan/apply tách rời lâu khiến lock không bảo vệ được drift sau plan.

## Khi nào chưa cần hoặc dễ over-engineer

- Lab một người dùng local state có thể chưa cần lock backend.
- Không nên force-unlock nếu chưa xác minh không còn process đang apply.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Remote State]] vì state locking thường đi cùng remote backend.
- [[Terraform Plan]] vì plan/apply phụ thuộc state nhất quán.
- [[Terraform Apply]] vì apply ghi state và cần lock.
- [[Config Drift]] vì state lock không thay thế drift review.

## Liên quan rộng

- IaC backend
- Concurrent apply
- State corruption

## Keywords / Từ khóa tìm kiếm

- State Locking
- Terraform state locking
- remote state lock
- force unlock
- state backend
- concurrent apply
- state locking debugging

## Source trace

- Terraform documentation
- OpenTofu documentation
