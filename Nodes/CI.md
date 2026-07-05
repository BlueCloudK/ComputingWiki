# CI

Aliases: Continuous Integration, tích hợp liên tục

Type: Deployment / Operations

## Context / Ngữ cảnh

CI xuất hiện khi code thay đổi liên tục và team cần feedback tự động trước khi merge hoặc release. Nó đặc biệt quan trọng khi nhiều người cùng sửa repo, có test/regression suite, build artifact, lint/static check hoặc nhiều môi trường runtime.

## Boundary / Ranh giới

### Nó là gì

CI là practice tự động checkout code, install dependency, build, lint/static check, chạy test và publish kết quả mỗi khi push hoặc mở pull request. Mục tiêu là phát hiện lỗi sớm và giữ main branch luôn ở trạng thái có thể tiếp tục phát triển.

### Nó không phải là gì

CI không phải CD. CI tạo confidence cho code và artifact; CD đưa artifact tới environment. CI cũng không thay thế test tốt: pipeline xanh nhưng test rỗng, flaky hoặc thiếu path quan trọng thì vẫn không đáng tin.

## Core Mechanism / Cơ chế lõi

Workflow CI được trigger bởi push/PR. Runner lấy code, cache dependency nếu phù hợp, chạy các job như install, build, unit test, integration test, coverage, security scan, rồi trả status check. Branch protection có thể yêu cầu check xanh trước merge.

## Project Role / Vai trò trong dự án

CI là lớp feedback loop cho refactor, regression và collaboration. Nó giúp repo phát hiện lỗi trước khi code vào main, giữ build reproducible, và tạo baseline cho deployment/CD sau đó.

## Output / Artifact nên có

- CI workflow config và trigger rule
- Required checks trước merge: build, test, lint, coverage nếu cần
- Artifact/log/report: test report, coverage, build output
- Cache policy cho dependency/build nếu cần tốc độ
- Flaky test policy và owner xử lý pipeline đỏ

## Decision Checklist / Câu hỏi kiểm tra

- Check nào bắt buộc trước merge?
- Pipeline có đủ nhanh để dev không bypass không?
- Test nào chạy ở PR, test nào chạy nightly?
- Secret/permission trong CI có scope tối thiểu không?
- Cache có làm build sai hoặc dùng dependency cũ không?
- Khi fail, log/artifact có đủ debug không?
- Branch protection có phản ánh risk thật không?

## Failure Modes / Cách nó gây lỗi

- Pipeline flaky làm team mất niềm tin và ignore màu đỏ.
- CI xanh nhưng không chạy test path quan trọng.
- Secret CI bị lộ qua log hoặc dùng quyền quá rộng.
- Cache sai làm build pass/fail không deterministic.
- Pipeline quá chậm khiến dev tìm cách bypass.
- Required checks thiếu nên code chưa build vẫn merge vào main.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo thử nghiệm một người có thể bắt đầu bằng script test local trước.
- Không nên thêm quá nhiều stage nếu không tăng confidence thật.
- Không nên bắt full E2E nặng ở mọi commit nếu smoke/unit/integration đủ cho PR.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Test Coverage]] vì coverage report/gate thường chạy trong CI.
- [[Regression Test]] vì regression suite cần CI để bắt bug quay lại.
- [[CD]] vì CD thường dùng artifact và signal từ CI.
- [[GitHub Actions]] vì GitHub Actions là tool phổ biến để chạy CI trong repo GitHub.
- [[Build Cache]] vì cache ảnh hưởng tốc độ và độ ổn định pipeline.

## Liên quan rộng

- Build automation
- Pull request checks
- Quality gates
- Developer feedback loop

## Keywords / Từ khóa tìm kiếm

- CI
- Continuous Integration
- tích hợp liên tục
- build verification
- automated test pipeline
- merge check
- pull request checks
- branch protection
- CI pipeline
- flaky CI
- CI cache
- CI debugging

## Source trace

- Continuous Delivery
- GitHub Actions documentation
