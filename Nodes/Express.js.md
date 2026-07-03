# Express.js

Aliases: Express, Express.js, Node.js web framework

Type: Framework / Backend

## Context / Ngữ cảnh

Express.js là web framework tối giản cho Node.js, thường dùng để dựng API, middleware pipeline và server-side routing.

## Boundary / Ranh giới

### Nó là gì

Nó là routing/middleware layer trên HTTP server của Node.js, cho phép xử lý request, response, error và plugin middleware.

### Nó không phải là gì

Nó không cung cấp opinion mạnh về architecture, validation, ORM, auth hoặc dependency injection.

## Core Mechanism / Cơ chế lõi

Request đi qua chuỗi middleware theo thứ tự đăng ký. Route handler hoặc error middleware quyết định response cuối cùng.

## Project Role / Vai trò trong dự án

Node này giúp debug route order, body parser, async error handling, CORS, auth middleware và boundary giữa controller/service trong Node backend.

## Output / Artifact nên có

- Route table hoặc API map
- Middleware order note
- Error handler cuối pipeline

## Decision Checklist / Câu hỏi kiểm tra

- Middleware có chạy trước route cần bảo vệ không?
- Async error có được chuyển tới error handler không?
- Body size, upload và CORS có giới hạn rõ không?
- Route order có làm route tổng quát nuốt route cụ thể không?

## Failure Modes / Cách nó gây lỗi

- Quên `next(error)` hoặc async wrapper làm lỗi bị nuốt
- Middleware order sai làm auth/CORS/body parser fail
- Không giới hạn body/upload gây resource exhaustion

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần Express nếu chỉ cần serverless handler rất nhỏ
- Dễ over-engineer nếu tự dựng framework layer lớn thay vì giữ route/service rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Middleware]] vì Express xoay quanh middleware chain
- [[Route]] vì route matching là phần chính của framework

## Liên quan rộng

- Node.js backend
- REST API
- Web server

## Keywords / Từ khóa tìm kiếm

- Express.js
- Express
- Node.js framework
- express middleware
- express router
- route handler
- async error handling
- Node backend

## Source trace

- Express official documentation
- Node.js documentation
