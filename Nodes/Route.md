# Route

Aliases: routing, URL route, định tuyến request

Type: Backend / Web Development

## Context / Ngữ cảnh

Route xuất hiện khi URL, HTTP method hoặc navigation path cần được map tới handler, controller, page, component hoặc upstream service tương ứng. Nó nằm ở boundary giữa request từ client và phần code thật xử lý request đó.

## Boundary / Ranh giới

### Nó là gì

Route là rule định tuyến request: pattern nào match path/method nào, route parameter nào được parse, middleware nào chạy và handler nào nhận request. Trong backend, route thường map tới controller/action. Trong frontend, route map URL tới page/component và data-loading behavior.

### Nó không phải là gì

Route không phải toàn bộ API contract. Route chỉ nói request đi đâu; contract còn cần request/response schema, auth, validation, error format và side effect. Route cũng không nên chứa business logic chính; nếu route config quá thông minh, debug sẽ khó vì behavior nằm trong routing layer thay vì handler/use case.

## Core Mechanism / Cơ chế lõi

Router so sánh request path/method với route table theo priority/order, parse params/query, chạy middleware/guard, rồi gọi handler hoặc fallback/404. Các yếu tố quan trọng gồm path pattern, dynamic segment, wildcard, route order, method matching, trailing slash, base path, version prefix và nested routes.

## Project Role / Vai trò trong dự án

Route là node cần mở khi endpoint/page không vào đúng handler, 404 lạ, route dynamic bắt nhầm route static, middleware không chạy, frontend refresh mất page hoặc reverse proxy/gateway chuyển path sai. Nó giúp team trace request từ URL → proxy/gateway → router → controller/page.

## Output / Artifact nên có

- Route map: method/path → middleware/guard → handler/controller/page
- Route parameter convention và validation rule
- Fallback/404/redirect behavior
- API version/base path decision nếu có nhiều version hoặc service prefix
- Test case cho static route, dynamic route, wildcard, unauthorized và not found

## Decision Checklist / Câu hỏi kiểm tra

- Route có match đúng method và path không?
- Dynamic route có bắt nhầm static route không?
- Route order/priority có rõ trong framework đang dùng không?
- Middleware/auth guard có chạy trước handler không?
- Route param có được validate trước khi vào service không?
- Base path/proxy prefix có bị rewrite sai không?
- Fallback 404/redirect có phân biệt API route và frontend route không?

## Failure Modes / Cách nó gây lỗi

- Route order sai làm `/users/new` bị bắt bởi `/users/:id`.
- Thiếu method matching làm POST/GET đi nhầm handler hoặc trả 405/404 khó hiểu.
- Proxy rewrite/base path sai làm app route không match production dù local chạy.
- Frontend SPA route refresh trả 404 vì web server không fallback đúng.
- Middleware không gắn route nhạy cảm làm thiếu auth/authorization.
- Wildcard route quá rộng che route cụ thể và làm debug khó.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ ít endpoint/page có thể dùng route trực tiếp, chưa cần route generator/phân tầng quá nhiều.
- Không nên encode business workflow vào route structure nếu domain logic nằm tốt hơn ở service/use case.
- Không nên tạo route versioning phức tạp khi chưa có consumer ổn định cần backward compatibility.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Endpoint]] vì route thường là cách endpoint được map tới handler.
- [[Controller]] vì backend route thường gọi controller/action.
- [[Middleware]] vì middleware/guard thường chạy theo route.
- [[Reverse Proxy]] vì proxy rewrite/base path có thể làm route match sai.
- [[SPA]] vì frontend route và server fallback cần phối hợp để tránh refresh 404.

## Liên quan rộng

- Web framework
- Request handling
- Frontend navigation
- API design

## Keywords / Từ khóa tìm kiếm

- Route
- routing
- URL route
- định tuyến request
- route matching
- path pattern
- dynamic route
- route parameter
- route order
- wildcard route
- middleware route
- API route
- frontend route
- 404 route debugging
- base path rewrite

## Source trace

- Express routing documentation
- MDN HTTP documentation
