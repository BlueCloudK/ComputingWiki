# Deployment

Aliases: release, rollout, triển khai

Type: Reliability / SRE

## Context / Ngữ cảnh

Deployment xuất hiện khi code/config/artifact cần được đưa từ môi trường build/test ra staging hoặc production. Nó là bước biến phần mềm đã viết thành service đang chạy thật, có traffic, config, health check, log, monitoring và rollback path.

## Boundary / Ranh giới

### Nó là gì

Deployment là quá trình phát hành một version vào môi trường chạy: build artifact, publish image/package, apply config, run migration nếu có, start/update service, verify health và expose traffic. Deployment tốt phải repeatable, observable và có rollback/mitigation rõ.

### Nó không phải là gì

Deployment không phải chỉ là copy file hoặc bấm nút deploy. Nếu thiếu environment config, health check, monitoring, database migration plan và rollback, release vẫn rủi ro cao. Deployment cũng không đồng nghĩa với CI/CD toàn bộ; nó là phần đưa version vào runtime.

## Core Mechanism / Cơ chế lõi

Pipeline hoặc operator chọn artifact version, áp dụng config/env/secrets, cập nhật runtime như container/Kubernetes/service, chờ readiness, chạy smoke test, rồi mở traffic theo deployment strategy. Sau deploy, monitoring xác minh error/latency/user flow trước khi coi release thành công.

## Project Role / Vai trò trong dự án

Deployment là node cần mở khi chuẩn bị production, debug “local chạy nhưng server lỗi”, hoặc thiết kế release process. Nó giúp team kiểm tra version nào đang chạy, config nào được dùng, dependency nào cần sẵn, signal nào xác nhận deploy ổn và rollback ra sao.

## Output / Artifact nên có

- Deployment manifest/script/pipeline: artifact, command, environment, owner
- Environment/config/secret checklist
- Health check/readiness và smoke test sau deploy
- Deployment strategy: rolling, blue-green, canary hoặc manual rollout
- Rollback plan và release notes/changelog
- Monitoring dashboard cho version mới: error rate, latency, logs, traffic

## Decision Checklist / Câu hỏi kiểm tra

- Artifact/version nào đang được deploy và có thể trace về commit nào?
- Config/secret/environment có đúng môi trường không?
- Database migration có cần chạy trước/sau app và có backward compatible không?
- Health check/readiness có đủ để nhận traffic không?
- Smoke test nào chứng minh path chính chạy được?
- Rollback hoặc forward fix mất bao lâu nếu lỗi?
- Monitoring sau deploy có chỉ ra version mới đang ổn hay không?

## Failure Modes / Cách nó gây lỗi

- Deploy nhầm version hoặc nhầm environment.
- Config/secret khác staging làm production lỗi dù build giống nhau.
- Health check xanh nhưng user flow chính hỏng.
- Migration phá backward compatibility làm rollback app code không đủ.
- Không drain traffic làm request đang xử lý bị cắt khi replace instance.
- Không có monitoring theo version nên lỗi chỉ phát hiện qua user report.

## Khi nào chưa cần hoặc dễ over-engineer

- App thử nghiệm chưa có user thật có thể deploy thủ công đơn giản.
- Không nên xây pipeline phức tạp nếu team chưa có nhu cầu release thường xuyên.
- Không nên tự động hóa deploy production khi chưa có rollback, health check và monitoring tối thiểu.

## Gồm những gì

- [[Rollback]]
- [[Environment Variable]]

## Nối mạnh

- [[Deployment Strategy]] vì strategy quyết định cách version mới nhận traffic.
- [[Rollback]] vì deployment an toàn cần đường quay lại rõ.
- [[Health Check]] vì deploy cần signal ready/healthy trước khi nhận traffic.
- [[Monitoring]] vì deploy cần metric/log để verify version mới.
- [[Config Drift]] vì deployment phải kiểm soát runtime config khớp source of truth.

## Liên quan rộng

- Release engineering
- CI/CD
- Production operations
- Change management

## Keywords / Từ khóa tìm kiếm

- Deployment
- release
- rollout
- triển khai
- deploy artifact
- deployment pipeline
- production deploy
- environment config
- smoke test
- readiness check
- release verification
- rollback plan
- deployment debugging
- operational readiness

## Source trace

- Continuous Delivery
- SWEBOK Operations
- Google SRE Books
