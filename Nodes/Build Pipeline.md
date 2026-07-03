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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

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
