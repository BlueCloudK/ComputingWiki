# Django

Aliases: Django, Django framework, Python web framework

Type: Framework / Backend

## Context / Ngữ cảnh

Django là Python web framework opinionated cho web app và backend, nổi bật với ORM, admin, auth, migrations và MTV structure.

## Boundary / Ranh giới

### Nó là gì

Nó là full-stack server framework quản lý URL routing, view, model/ORM, template, form, auth và migration.

### Nó không phải là gì

Nó không thay thế hiểu biết về database schema, query performance, permission model hoặc deployment security.

## Core Mechanism / Cơ chế lõi

Request được map qua URLconf tới view, view dùng model/ORM/service rồi trả response/template/API. Migration quản lý schema evolution.

## Project Role / Vai trò trong dự án

Node này giúp debug Django app qua URL routing, ORM query, migration conflict, middleware, settings và permission/auth behavior.

## Output / Artifact nên có

- URL route map
- Model/migration history rõ
- Settings phân tách theo environment

## Decision Checklist / Câu hỏi kiểm tra

- Query ORM có tạo N+1 không?
- Migration có tương thích production data không?
- Middleware/auth permission có chạy đúng thứ tự không?
- Settings secret/debug mode có an toàn ở production không?

## Failure Modes / Cách nó gây lỗi

- N+1 query do relation lazy loading
- Migration conflict hoặc migration phá dữ liệu production
- `DEBUG=True` hoặc secret/config sai ở production

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần Django nếu chỉ làm một API nhỏ cực nhẹ
- Dễ over-engineer nếu dùng app/model quá dày cho domain chưa rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ORM]] vì Django ORM là phần trung tâm của framework
- [[Database Migration]] vì migration là artifact production quan trọng

## Liên quan rộng

- Python backend
- Web application
- Admin interface

## Keywords / Từ khóa tìm kiếm

- Django
- Django framework
- Python web framework
- Django ORM
- Django migration
- URLconf
- Django settings
- Django admin

## Source trace

- Django official documentation
