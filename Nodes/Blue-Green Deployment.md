# Blue-Green Deployment

Aliases: blue green release, triển khai blue-green, blue/green deployment, triển khai xanh lam xanh lá

Type: Deployment / Operations

## Context / Ngữ cảnh

Blue-Green Deployment xuất hiện khi cần chuyển traffic giữa hai environment/version để giảm downtime và rollback nhanh.

## Boundary / Ranh giới

### Nó là gì

Blue-Green Deployment là strategy có hai environment tương đương: một live, một chuẩn bị version mới.

### Nó không phải là gì

Nó không tự giải quyết database migration phức tạp và không phù hợp nếu cost chạy đôi quá cao.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là deploy vào idle environment, verify, switch traffic, giữ old environment để rollback.

## Project Role / Vai trò trong dự án

Node này giúp release an toàn hơn khi cần cutover rõ ràng.

## Output / Artifact nên có

- Blue/green environment inventory
- Traffic switch plan
- Database compatibility/rollback note

## Decision Checklist / Câu hỏi kiểm tra

- Blue và green có thật sự tương đương không?
- Switch traffic có atomic/observable không?
- Schema migration có cho phép quay lại blue không?

## Failure Modes / Cách nó gây lỗi

- Green khác config nên chỉ lỗi sau cutover
- Switch traffic nhưng session/cache không tương thích
- DB migration phá rollback

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu một rolling deploy đơn giản đủ
- Dễ over-engineer nếu cost chạy đôi lớn hơn risk release

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Deployment Strategy]] vì blue-green là một strategy
- [[Rollback]] vì rollback thường là switch traffic về environment cũ

## Liên quan rộng

- Zero-downtime release

## Keywords / Từ khóa tìm kiếm

- Blue-Green Deployment
- blue green release
- traffic switch
- zero downtime deployment
- rollback by switch
- parallel environment
- triển khai blue green

## Source trace

- Continuous Delivery
