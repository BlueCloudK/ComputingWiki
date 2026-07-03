# Rails

Aliases: Ruby on Rails, Rails, RoR

Type: Framework / Backend

## Context / Ngữ cảnh

Rails là Ruby web framework opinionated theo convention over configuration, dùng MVC, Active Record, migrations và routing.

## Boundary / Ranh giới

### Nó là gì

Nó là framework cho web app/API Ruby, gom routing, controller, model/ORM, view, migration, background jobs và asset integration.

### Nó không phải là gì

Nó không tự tránh được fat model/controller, N+1 query hoặc migration rủi ro nếu team không giữ boundary rõ.

## Core Mechanism / Cơ chế lõi

Request được route tới controller action, controller gọi model/service, Active Record truy cập database và response trả qua view/serializer/API.

## Project Role / Vai trò trong dự án

Node này giúp đọc Rails app, debug route/controller, Active Record relation, migration, callback, validation và production performance.

## Output / Artifact nên có

- Route map
- Model association và migration history
- Query/performance note cho endpoint nặng

## Decision Checklist / Câu hỏi kiểm tra

- Relation có eager load để tránh N+1 không?
- Callback có tạo side effect ẩn không?
- Migration có lock table hoặc downtime risk không?
- Controller có giữ business logic quá nhiều không?

## Failure Modes / Cách nó gây lỗi

- N+1 query do Active Record association
- Callback ẩn làm side effect khó debug
- Migration production lock bảng lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần Rails nếu chỉ cần worker hoặc API cực nhỏ
- Dễ over-engineer nếu lạm dụng callback/magic thay vì flow rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Active Record]] vì Rails dùng Active Record làm data access chính
- [[Model View Controller]] vì Rails tổ chức web app quanh MVC

## Liên quan rộng

- Ruby backend
- Web application
- Database migration

## Keywords / Từ khóa tìm kiếm

- Rails
- Ruby on Rails
- RoR
- Active Record
- Rails migration
- Rails route
- Rails controller
- convention over configuration

## Source trace

- Ruby on Rails Guides
