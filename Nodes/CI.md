# CI

Aliases: Continuous Integration, tích hợp liên tục

Type: Deployment / Operations

## Context / Ngữ cảnh

CI xuất hiện khi nhiều thay đổi code cần được merge thường xuyên mà vẫn giữ build/test feedback nhanh và đáng tin.

## Boundary / Ranh giới

### Nó là gì

CI là practice tự động build, test và kiểm tra code mỗi khi thay đổi được push hoặc mở pull request.

### Nó không phải là gì

Nó không phải CD, không thay thế test tốt, và không có giá trị nếu pipeline chậm/flaky đến mức team bỏ qua.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là feedback loop: checkout code, install dependency, build, run test/static check, publish result và chặn merge nếu signal đỏ.

## Project Role / Vai trò trong dự án

CI giúp phát hiện regression sớm và tạo baseline tin cậy trước khi deploy. Nó là lớp an toàn cho refactor, API change và collaboration.

## Output / Artifact nên có

- CI workflow/pipeline
- Build/test/lint result
- Branch protection hoặc merge rule nếu phù hợp

## Decision Checklist / Câu hỏi kiểm tra

- Check nào phải chạy trước merge?
- Pipeline có đủ nhanh để dev tin dùng không?
- Test flaky được xử lý hay bị bỏ qua?
- Secret trong CI có được giới hạn quyền không?
- Artifact/log có đủ debug khi fail không?

## Failure Modes / Cách nó gây lỗi

- Pipeline flaky làm team mất niềm tin
- CI xanh nhưng không test path quan trọng
- Secret CI bị lộ hoặc dùng quyền quá rộng
- Pipeline quá chậm khiến dev tìm cách bypass

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần CI phức tạp cho repo thử nghiệm một người rất nhỏ
- Dễ over-engineer nếu pipeline nhiều stage nhưng không tăng confidence thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Test Coverage]] vì CI cần test đủ ý nghĩa để bắt regression
- [[Regression Test]] vì regression suite thường chạy trong CI
- [[CD]] vì CD thường bắt đầu từ artifact và confidence do CI tạo ra

## Liên quan rộng

- Build automation
- Pull request checks
- Quality gates

## Source trace

- Continuous Delivery
- GitHub Actions docs
