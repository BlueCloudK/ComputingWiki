# ASP.NET Core

Aliases: ASP.NET Core, dotnet web framework, .NET backend framework

Type: Framework / Backend

## Context / Ngữ cảnh

ASP.NET Core là framework .NET để xây web API, MVC app, realtime service và backend chạy cross-platform.

## Boundary / Ranh giới

### Nó là gì

Nó cung cấp middleware pipeline, routing, dependency injection, configuration, hosting và integration với .NET runtime.

### Nó không phải là gì

Nó không tự giải quyết domain design, database consistency, authentication policy hoặc deployment hardening.

## Core Mechanism / Cơ chế lõi

Request đi qua middleware pipeline, được route tới endpoint/controller/minimal API, rồi response quay ngược pipeline trước khi trả client.

## Project Role / Vai trò trong dự án

Node này giúp debug request pipeline, middleware order, DI lifetime, config provider và production hosting cho service .NET.

## Output / Artifact nên có

- Middleware pipeline rõ thứ tự
- Endpoint/controller map
- Appsettings/profile config cho từng environment

## Decision Checklist / Câu hỏi kiểm tra

- Middleware authentication/authorization đặt đúng thứ tự chưa?
- DI service dùng singleton/scoped/transient có đúng lifetime không?
- Endpoint có validate input và trả error contract ổn định không?
- Config secret có bị commit vào appsettings không?

## Failure Modes / Cách nó gây lỗi

- Middleware order sai làm auth hoặc CORS không chạy như tưởng
- Scoped service bị dùng trong singleton gây lỗi runtime
- Environment config lệch làm production behavior khác local

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần framework full nếu chỉ cần tool CLI hoặc worker rất nhỏ
- Dễ over-engineer nếu tạo nhiều layer service/repository cho CRUD đơn giản chưa có complexity

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Middleware]] vì request pipeline là cơ chế trung tâm của ASP.NET Core
- [[Dependency Injection]] vì framework tích hợp DI mặc định

## Liên quan rộng

- .NET backend
- Web API
- Cloud deployment

## Keywords / Từ khóa tìm kiếm

- ASP.NET Core
- dotnet web
- .NET backend
- middleware pipeline
- minimal API
- Kestrel
- appsettings
- DI lifetime

## Source trace

- Microsoft ASP.NET Core documentation
