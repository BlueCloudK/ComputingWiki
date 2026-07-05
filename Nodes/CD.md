# CD

Aliases: Continuous Delivery, Continuous Deployment, triển khai liên tục

Type: Deployment / Operations

## Context / Ngữ cảnh

CD xuất hiện khi artifact đã qua CI cần được đưa tới staging/production một cách lặp lại, kiểm soát được và ít thao tác tay. Nó giúp release nhỏ hơn, thường xuyên hơn, có verification và rollback rõ hơn.

## Boundary / Ranh giới

### Nó là gì

CD là practice tự động hóa release/deployment pipeline. Continuous Delivery nghĩa là artifact luôn sẵn sàng deploy với approval nếu cần; Continuous Deployment nghĩa là change đạt gate sẽ tự deploy production. Cả hai đều cần verification, monitoring và rollback/mitigation.

### Nó không phải là gì

CD không phải chỉ copy file lên server. CD cũng không bắt buộc auto-deploy mọi commit lên production. Nếu thiếu health check, smoke test, rollback, migration compatibility và monitoring, pipeline tự động chỉ làm lỗi lan nhanh hơn.

## Core Mechanism / Cơ chế lõi

Pipeline lấy artifact/version đã build, promote qua environment, apply config/secret/migration nếu cần, deploy workload, chờ readiness, chạy smoke test, mở traffic theo deployment strategy, rồi monitor signal như error rate, latency, health và business metric. Nếu signal xấu, pipeline pause/rollback hoặc yêu cầu approval.

## Project Role / Vai trò trong dự án

CD biến deployment thành quy trình repeatable thay vì thao tác thủ công khó nhớ. Nó giúp team trace version nào đang ở môi trường nào, ai approve, signal nào pass/fail và rollback bằng cách nào.

## Output / Artifact nên có

- Deployment pipeline với stage: build artifact, staging, production, verification
- Promotion/approval rule theo environment
- Smoke test và post-deploy verification
- Rollback/roll-forward plan trong pipeline
- Release artifact/version trace về commit và config
- Deployment logs và monitoring link

## Decision Checklist / Câu hỏi kiểm tra

- Artifact có immutable và trace được về commit không?
- Environment promotion cần approval ở đâu?
- Deploy có chạy migration/config change không?
- Smoke test và health check sau deploy là gì?
- Rollback có tự động, thủ công hay cần approval?
- Pipeline có dừng khi SLO/error/latency xấu không?
- Secret/permission của deploy runner có quá rộng không?

## Failure Modes / Cách nó gây lỗi

- Auto deploy production nhưng không verify user impact.
- Artifact không reproducible làm rollback khó.
- Pipeline thiếu approval cho change rủi ro cao.
- Deploy thành công ở pipeline nhưng runtime lỗi vì config/secret khác.
- Migration không backward compatible làm rollback app code không đủ.
- Deploy runner có quyền quá rộng, lộ token là lộ production.

## Khi nào chưa cần hoặc dễ over-engineer

- Release hiếm, app nhỏ, deploy thủ công có checklist tốt có thể đủ giai đoạn đầu.
- Không nên build pipeline nhiều gate nếu team không dùng signal để quyết định.
- Không nên bật continuous deployment production trước khi CI/test/monitoring/rollback đủ tin.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì CD dựa vào artifact và confidence từ CI.
- [[Deployment]] vì CD tự động hóa deployment process.
- [[Deployment Strategy]] vì CD cần biết rollout/traffic strategy.
- [[Rollback]] vì production pipeline cần đường quay lại rõ.
- [[Monitoring]] vì deploy decision cần signal sau release.

## Liên quan rộng

- Release automation
- Progressive delivery
- Environment promotion
- DevOps workflow

## Keywords / Từ khóa tìm kiếm

- CD
- Continuous Delivery
- Continuous Deployment
- triển khai liên tục
- release pipeline
- deployment automation
- promotion pipeline
- production approval
- smoke test
- post deploy verification
- deployment rollback
- CD debugging

## Source trace

- Continuous Delivery
- Google SRE Books
