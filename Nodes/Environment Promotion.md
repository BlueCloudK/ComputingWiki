# Environment Promotion

Aliases: Environment Promotion, promotion between environments

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Environment Promotion xuất hiện khi cùng một release artifact/config cần được đưa lần lượt qua dev, staging, pre-prod và production theo gate rõ.

## Boundary / Ranh giới

### Nó là gì

Environment Promotion là workflow promote một version đã build/test từ environment thấp lên environment cao hơn mà không rebuild tùy ý ở mỗi bước.

### Nó không phải là gì

Environment Promotion không phải deploy lại từ source mỗi lần. Nếu mỗi environment build artifact khác nhau, traceability và rollback sẽ yếu hơn.

## Core Mechanism / Cơ chế lõi

CI tạo artifact từ commit. CD deploy artifact đó vào dev/staging, chạy test/approval, rồi promote cùng artifact hoặc manifest version lên production. Metadata ghi environment nào đang chạy version nào.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế release pipeline, approval gate, rollback, config per environment hoặc audit vì sao production chạy version khác staging.

## Output / Artifact nên có

- Artifact/version to promote
- Environment sequence
- Promotion gate/checklist
- Config difference note
- Rollback rule

## Decision Checklist / Câu hỏi kiểm tra

- Cùng artifact có được dùng qua các environment không?
- Gate nào cần pass trước khi promote?
- Config khác nhau ở đâu và có kiểm soát không?
- Ai được approve promotion lên production?
- Rollback quay về artifact/version nào?

## Failure Modes / Cách nó gây lỗi

- Rebuild giữa staging và production làm kết quả không còn giống nhau.
- Config drift khiến staging pass nhưng production fail.
- Promotion không ghi audit nên không biết ai đưa version nào lên.
- Approval chỉ hình thức, thiếu test/metric context.
- Rollback không có artifact/version cũ.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype một môi trường có thể deploy trực tiếp trước.
- Không nên thêm nhiều stage nếu không có test/gate thật ở mỗi stage.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Release Artifact]] vì promotion nên dùng artifact đã build sẵn.
- [[CD]] vì promotion là phần của delivery pipeline.
- [[Deployment Approval]] vì environment cao thường cần approval.
- [[Config Drift]] vì khác biệt config giữa environment dễ gây lỗi.

## Liên quan rộng

- Release pipeline
- Staging production parity
- Promotion gate

## Keywords / Từ khóa tìm kiếm

- Environment Promotion
- promotion between environments
- staging to production
- release promotion
- artifact promotion
- promotion gate
- environment promotion debugging

## Source trace

- Continuous Delivery
- GitHub Actions documentation
