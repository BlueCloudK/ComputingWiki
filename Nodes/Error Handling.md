# Error Handling

Aliases: exception handling, error response, xử lý lỗi

## Dùng trong dự án để làm gì

Error Handling dùng khi nhiều phần mềm cần giao tiếp ổn định với nhau. Trong dự án, nó quyết định contract, dữ liệu vào ra, lỗi tích hợp và khả năng thay đổi giữa frontend, backend, service hoặc third-party.

## Khi nào cần quan tâm

- Thiết kế hoặc thay đổi endpoint/contract
- Frontend-backend hoặc service-service hiểu dữ liệu khác nhau
- Tích hợp third-party/webhook/RPC

## Lỗi / rủi ro thường gặp

- Breaking change làm client hoặc service khác lỗi
- Request/response thiếu validation và versioning
- Error handling không thống nhất gây khó debug

## Gồm những gì

- [[Logging]]
- [[Response]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- SWEBOK Map / API and Integration
