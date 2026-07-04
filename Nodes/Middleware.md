# Middleware

Aliases: HTTP middleware, request middleware, middleware backend

Type: Backend Engineering

## Context / Ngữ cảnh

Middleware xuất hiện khi backend cần chạy cross-cutting behavior trước hoặc sau handler chính của request, ví dụ logging, authentication, authorization, CORS, body parsing, rate limiting, tracing, compression hoặc error handling. Nó nằm trên request pipeline chứ không phải domain logic chính.

## Boundary / Ranh giới

### Nó là gì

Middleware là thành phần trong pipeline xử lý request/response. Nó nhận request, có thể đọc/sửa request, quyết định cho đi tiếp tới middleware/handler sau, hoặc dừng pipeline và trả response. Một middleware tốt có trách nhiệm rõ, thứ tự chạy rõ và failure behavior rõ.

### Nó không phải là gì

Middleware không phải nơi nhét business logic nghiệp vụ. Nếu middleware biết quá nhiều domain rule, database workflow hoặc side effect phức tạp, request pipeline sẽ khó test/debug. Middleware cũng không tự an toàn nếu order sai, ví dụ auth chạy sau handler hoặc error handler đặt sai vị trí.

## Core Mechanism / Cơ chế lõi

Framework tạo chain middleware. Request đi qua từng middleware theo thứ tự đăng ký. Middleware có thể pre-process, gọi `next`, rồi post-process response hoặc catch error. Thứ tự rất quan trọng: body parser trước validation, auth trước protected route, CORS trước response, error handler thường ở cuối pipeline.

## Project Role / Vai trò trong dự án

Middleware là node cần mở khi endpoint thiếu auth, CORS lỗi, request body không parse, logging/tracing thiếu request id, rate limit không ăn hoặc error không được map đúng. Nó giúp team trace request qua pipeline thay vì chỉ nhìn controller/handler.

## Output / Artifact nên có

- Middleware order map: global middleware, route middleware, error middleware
- Responsibility note cho từng middleware: input, output, side effect, stop condition
- Protected route/auth guard matrix
- Test case cho order: CORS preflight, auth fail, validation fail, error path
- Observability: request id, trace id, latency, status code, middleware error log

## Decision Checklist / Câu hỏi kiểm tra

- Middleware này chạy global hay chỉ trên một nhóm route?
- Thứ tự middleware có đúng không?
- Middleware có gọi next/continue đúng lúc không, hay dừng pipeline sai?
- Auth/authorization có chạy trước handler nhạy cảm không?
- Error trong middleware được catch/map ở đâu?
- Middleware có đọc request body nhiều lần hoặc phá stream không?
- Có side effect nào khiến retry hoặc request fail giữa pipeline gây lỗi không?

## Failure Modes / Cách nó gây lỗi

- Auth middleware không gắn vào route nhạy cảm làm endpoint lộ dữ liệu.
- Middleware order sai làm body chưa parse nhưng validation đã chạy.
- CORS/preflight xử lý sai làm browser chặn request dù backend logic đúng.
- Middleware không gọi next hoặc gọi next hai lần làm request treo/lỗi khó đoán.
- Error handler đặt sai vị trí làm exception thành 500 không chuẩn hoặc process crash.
- Logging/tracing middleware thiếu request id làm incident khó trace qua service.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ có thể dùng vài middleware rõ ràng thay vì abstraction chain phức tạp.
- Không nên biến middleware thành nơi xử lý domain workflow chỉ vì nó chạy trước controller.
- Không nên thêm middleware global nếu chỉ vài route cần behavior đó.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Route]] vì middleware thường được gắn global hoặc theo route.
- [[Controller]] vì middleware chạy trước/sau controller handler.
- [[Authentication]] vì auth thường được triển khai như middleware/guard.
- [[CORS]] vì CORS là middleware phổ biến ở API backend.
- [[Rate Limiting]] vì rate limit thường nằm ở middleware/gateway layer.

## Liên quan rộng

- Request pipeline
- Backend framework
- Cross-cutting concern
- API security

## Keywords / Từ khóa tìm kiếm

- Middleware
- HTTP middleware
- request middleware
- middleware backend
- request pipeline
- middleware order
- auth middleware
- error middleware
- CORS middleware
- body parser
- rate limit middleware
- tracing middleware
- middleware chain
- next function
- middleware debugging

## Source trace

- Express middleware documentation
- ASP.NET Core middleware documentation
