# Laravel

Aliases: Laravel, PHP web framework

Type: Framework / Backend

## Context / Ngữ cảnh

Laravel là PHP web framework cho web app và API, có routing, controller, Eloquent ORM, migrations, queue, auth và artisan tooling.

## Boundary / Ranh giới

### Nó là gì

Nó là application framework opinionated giúp tổ chức backend PHP theo route/controller/model/service/job.

### Nó không phải là gì

Nó không tự bảo đảm code sạch, query tốt hoặc security nếu validation, auth và data boundary bị dùng sai.

## Core Mechanism / Cơ chế lõi

Request đi qua middleware, route tới controller/action, dùng service/model/Eloquent và trả response/view/resource.

## Project Role / Vai trò trong dự án

Node này giúp debug route/middleware, Eloquent query, migration, queue job, config cache và auth/session trong Laravel app.

## Output / Artifact nên có

- Route list và middleware assignment
- Migration/schema rõ
- Queue/job config cho tác vụ nền

## Decision Checklist / Câu hỏi kiểm tra

- Middleware auth/csrf có áp đúng route group không?
- Eloquent relation có gây N+1 không?
- Config/cache có được refresh sau deploy không?
- Queue job có retry/idempotency phù hợp không?

## Failure Modes / Cách nó gây lỗi

- Route cache/config cache cũ làm deploy chạy behavior cũ
- Mass assignment hoặc validation thiếu gây lỗi bảo mật
- Queue retry tạo side effect trùng nếu job không idempotent

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần Laravel cho script PHP rất nhỏ
- Dễ over-engineer nếu mọi domain logic nằm trong model/controller quá dày

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ORM]] vì Eloquent ảnh hưởng mạnh tới data access và query behavior
- [[Background Job]] vì Laravel queue thường dùng cho side effect nền

## Liên quan rộng

- PHP backend
- Web application
- Queue processing

## Keywords / Từ khóa tìm kiếm

- Laravel
- PHP framework
- Eloquent ORM
- Laravel migration
- Laravel queue
- artisan
- route middleware
- PHP backend

## Source trace

- Laravel official documentation
