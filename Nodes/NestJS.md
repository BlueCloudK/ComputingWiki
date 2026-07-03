# NestJS

Aliases: NestJS, Nest.js, Nest framework

Type: Framework / Backend

## Context / Ngữ cảnh

NestJS là framework Node.js/TypeScript có kiến trúc module, controller, provider và dependency injection theo phong cách enterprise.

## Boundary / Ranh giới

### Nó là gì

Nó cung cấp structure cho backend TypeScript: module graph, DI container, decorators, guards, pipes, interceptors và adapters.

### Nó không phải là gì

Nó không tự làm domain model tốt; nếu module boundary sai thì Nest chỉ làm coupling trông có vẻ có cấu trúc hơn.

## Core Mechanism / Cơ chế lõi

Nest dựng module graph, resolve provider qua DI container, map controller route và chạy request qua pipe/guard/interceptor/filter.

## Project Role / Vai trò trong dự án

Node này giúp debug provider injection, module import/export, request lifecycle, validation pipe và auth guard trong TypeScript backend.

## Output / Artifact nên có

- Module map rõ import/export
- Provider ownership note
- Guard/pipe/interceptor order cho endpoint quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Provider được khai báo/export ở module đúng chưa?
- Module có phụ thuộc vòng không?
- Validation pipe có chạy trước business logic không?
- Guard và interceptor có làm thay đổi response contract không?

## Failure Modes / Cách nó gây lỗi

- Module import vòng làm provider resolve fail
- Decorator nhiều nhưng boundary domain vẫn lẫn lộn
- Global pipe/guard thay đổi behavior ngoài dự đoán

## Khi nào chưa cần hoặc dễ over-engineer

- Overkill cho API Node rất nhỏ chỉ vài route
- Dễ over-engineer nếu tạo module/provider cho mọi thứ mà không có domain boundary rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dependency Injection]] vì provider/module là cơ chế lõi của NestJS
- [[Controller]] vì request thường vào qua controller layer

## Liên quan rộng

- TypeScript backend
- Modular architecture
- API service

## Keywords / Từ khóa tìm kiếm

- NestJS
- Nest.js
- Nest framework
- TypeScript backend
- Nest module
- provider injection
- guard pipe interceptor
- decorator framework

## Source trace

- NestJS official documentation
