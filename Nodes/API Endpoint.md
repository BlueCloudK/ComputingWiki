# API Endpoint

Aliases: API Endpoint, endpoint, API endpoint, đường dẫn API

Type: Backend Engineering

## Context / Ngữ cảnh

API Endpoint xuất hiện khi client, frontend, mobile app, service nội bộ hoặc third-party cần gọi một operation cụ thể của backend qua URL/path/method. Nó là điểm chạm trực tiếp giữa API contract và code xử lý request.

## Boundary / Ranh giới

### Nó là gì

API Endpoint là một operation được expose qua API, thường xác định bởi method, path, request schema, response schema, auth requirement, status code và side effect. Ví dụ `GET /orders/{id}` và `POST /orders` là hai endpoint khác nhau vì hành vi và contract khác nhau.

### Nó không phải là gì

API Endpoint không chỉ là URL. Nếu thiếu method, input/output, auth, validation, error format và ownership thì chưa đủ để thiết kế hoặc test. Endpoint cũng không nên chứa toàn bộ business logic; nó thường chỉ nhận request, validate, gọi service/use case và trả response.

## Core Mechanism / Cơ chế lõi

Request đi vào router, match method/path, qua middleware như auth/rate limit/validation, rồi tới handler/controller. Handler parse input, gọi domain/service layer, map result/error thành HTTP response. Endpoint tốt phải rõ idempotency, side effect, status code, error format và compatibility với client.

## Project Role / Vai trò trong dự án

API Endpoint giúp team chia nhỏ backend thành các operation cụ thể để design, implement, test, document và debug. Khi incident xảy ra, endpoint là đơn vị để nhìn traffic, latency, error rate, auth failure, validation failure và breaking change ảnh hưởng client nào.

## Output / Artifact nên có

- Endpoint contract: method, path, request, response, error, auth, status codes
- Handler/controller ownership và service/use case được gọi
- Test case cho success, validation error, auth error, not found, conflict và timeout
- Observability: endpoint name, request id, latency, error rate, status code distribution
- Documentation/OpenAPI entry nếu endpoint public hoặc có nhiều consumer

## Decision Checklist / Câu hỏi kiểm tra

- Method/path có phản ánh đúng operation không?
- Request/response schema và required/optional fields có rõ không?
- Endpoint có cần authentication/authorization/scope nào không?
- Validation lỗi trả status code và error body thế nào?
- Operation có side effect không, có cần idempotency key không?
- Endpoint có versioning/backward compatibility requirement không?
- Có metric/log đủ để trace lỗi theo endpoint không?

## Failure Modes / Cách nó gây lỗi

- Endpoint thiếu validation làm dữ liệu bẩn đi vào service/database.
- Status code/error body không nhất quán làm frontend hoặc client SDK xử lý sai.
- Auth/authorization thiếu ở endpoint nhạy cảm làm lộ hoặc sửa dữ liệu trái phép.
- Handler chứa quá nhiều business logic làm khó test và reuse.
- Breaking change request/response làm client cũ hỏng.
- Không có endpoint-level metric khiến incident không biết API nào gây lỗi.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype một client một backend có thể document nhẹ, nhưng endpoint public hoặc nhiều consumer cần contract rõ.
- Không nên tạo endpoint quá nhỏ/vụn nếu mỗi endpoint chỉ bọc một field không có use case rõ.
- Không nên dùng một endpoint quá rộng kiểu “doEverything” vì sẽ phá validation, auth và observability.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Route]] vì route là rule match method/path tới endpoint handler.
- [[API Contract]] vì endpoint cần contract request/response/error rõ ràng.
- [[Request]] vì endpoint bắt đầu từ input HTTP/request.
- [[Response]] vì endpoint phải map result/error thành output cho client.

## Liên quan rộng

- Backend architecture
- API design
- Integration testing
- Observability

## Keywords / Từ khóa tìm kiếm

- API Endpoint
- endpoint
- API endpoint
- đường dẫn API
- HTTP endpoint
- method path
- endpoint handler
- controller action
- API route
- request schema
- response schema
- endpoint validation
- endpoint auth
- endpoint metrics
- API operation

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- OpenAPI Specification
