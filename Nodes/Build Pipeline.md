# Build Pipeline

Aliases: build pipeline, pipeline build

Type: Deployment / Operations

## Context / Ngữ cảnh

Build Pipeline xuất hiện khi source code cần được biến thành artifact kiểm chứng được trước release.

## Boundary / Ranh giới

### Nó là gì

Build Pipeline là chuỗi bước tự động build, test, package và publish artifact.

### Nó không phải là gì

Nó không phải deployment pipeline đầy đủ và không thay thế test meaningful.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chạy các stage theo thứ tự với dependency/cache/artifact rõ ràng.

## Project Role / Vai trò trong dự án

Node này giúp build reproducible và CI/CD đáng tin hơn.

## Output / Artifact nên có

- Pipeline stages: install, build, test, package, publish
- Artifact name/version/checksum
- Cache/dependency policy

## Decision Checklist / Câu hỏi kiểm tra

- Artifact có reproducible không?
- Stage nào tạo artifact deployable?
- Cache có thể làm build stale không?

## Failure Modes / Cách nó gây lỗi

- Build local khác CI
- Artifact không trace về commit
- Cache/dependency drift làm build lúc được lúc không

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần pipeline phức tạp cho repo thử nghiệm nhỏ
- Dễ over-engineer nếu nhiều stage nhưng không tăng confidence

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì build pipeline thường chạy trong CI
- [[CD]] vì CD consume artifact từ build pipeline

## Liên quan rộng

- Artifact management
- Build automation

## Source trace

- Continuous Delivery
- GitHub Actions docs
