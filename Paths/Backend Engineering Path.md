# Backend Engineering Path

## Mục tiêu

Path này giúp người đọc đi qua các khái niệm cần biết để hiểu và xây backend service từ request vào hệ thống tới vận hành production.

## Khi nào dùng path này

- Khi thiết kế backend service hoặc module API.
- Khi cần hiểu request đi qua các layer nào.
- Khi debug lỗi backend liên quan tới auth, validation, data hoặc performance.

## 1. Request đi vào hệ thống

- [[HTTP]] — nền để hiểu request/response giữa client và backend.
- [[Route]] — xác định request được map vào handler nào.
- [[Middleware]] — xử lý logic cắt ngang như auth, logging, CORS hoặc rate limit.
- [[Controller]] — nhận request ở tầng application và gọi logic phù hợp.
- [[Request Handler]] — nơi xử lý một request cụ thể thành response.
- [[Request Lifecycle]] — giúp nhìn toàn bộ đường đi của request.

## 2. Contract và input

- [[API Contract]] — thỏa thuận giữa client và backend về endpoint, schema và lỗi.
- [[Request Validation]] — chặn input sai trước khi đi vào business logic.
- [[Data Transfer Object]] — format dữ liệu đi qua boundary của application.
- [[Error Response]] — giúp client xử lý lỗi ổn định thay vì parse message tự do.
- [[API Error Code]] — chuẩn hóa failure case để client/backend debug được.

## 3. Business logic

- [[Service Layer]] — nơi đặt workflow nghiệp vụ không nên nhồi vào controller.
- [[Domain Model]] — mô hình hóa khái niệm nghiệp vụ cốt lõi.
- [[Repository]] — boundary giữa business logic và data access.
- [[Dependency Injection]] — giúp ghép dependency rõ ràng và test dễ hơn.
- [[Error Handling]] — quyết định lỗi được catch, translate và trả ra thế nào.

## 4. Data layer

- [[ORM]] — map giữa object/application model và database.
- [[Database Schema]] — cấu trúc lưu dữ liệu thật.
- [[Transaction]] — bảo vệ nhiều thao tác dữ liệu cần commit/rollback cùng nhau.
- [[Database Index]] — giúp query nhanh hơn khi dữ liệu lớn.
- [[Connection Pooling]] — quản lý connection để backend không tự bóp nghẽn database.

## 5. Auth, session và permission

- [[Authentication]] — xác định user/client là ai.
- [[Authorization]] — xác định user/client được phép làm gì.
- [[JWT]] — token format thường gặp trong API auth.
- [[Cookie]] — cơ chế lưu trạng thái/session phía browser.
- [[Session Management]] — quản lý phiên đăng nhập và lifecycle của session.

## 6. Production concerns

- [[Logging]] — ghi lại signal để debug và audit.
- [[Monitoring]] — theo dõi health và behavior của service.
- [[Latency]] — đo thời gian phản hồi user nhìn thấy.
- [[Rate Limiting]] — bảo vệ backend khỏi abuse hoặc overload.
- [[Graceful Shutdown]] — tránh mất request/job khi deploy hoặc scale down.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Domain service
- Application service
- Request context
- API pagination contract
- Backend configuration module

## Related paths

- [[API Design Path]]
- [[Database Engineering Path]]
- [[Security Engineering Path]]
- [[Debugging and Failure Patterns Path]]
