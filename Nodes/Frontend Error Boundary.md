# Frontend Error Boundary

Aliases: Frontend Error Boundary, error boundary

Type: Frontend Framework

## Context / Ngữ cảnh

Frontend Error Boundary xuất hiện khi UI cần bắt lỗi render/runtime ở một vùng giao diện để tránh làm sập toàn bộ app và hiển thị fallback có kiểm soát.

## Boundary / Ranh giới

### Nó là gì

Frontend Error Boundary là boundary xử lý lỗi ở UI tree, thường bắt exception trong render/lifecycle của component con và render fallback UI.

### Nó không phải là gì

Error Boundary không thay thế validation, logging hoặc backend error handling. Nó cũng không bắt mọi lỗi như async callback, event handler hoặc network failure nếu framework không hỗ trợ trực tiếp.

## Core Mechanism / Cơ chế lõi

Framework phát hiện lỗi trong subtree, chuyển lỗi tới boundary gần nhất, boundary ghi log/report và render fallback thay vì để cả app trắng màn hình.

## Project Role / Vai trò trong dự án

Dùng node này khi debug white screen, component crash, fallback UI, route-level resilience hoặc observability frontend production.

## Output / Artifact nên có

- Boundary placement map
- Fallback UI design
- Error reporting/logging rule
- Retry/reset behavior
- Test case cho component crash

## Decision Checklist / Câu hỏi kiểm tra

- Boundary đặt ở app-level, route-level hay widget-level?
- Fallback có đủ thông tin cho user không?
- Error có được log với context không?
- Có cơ chế retry/reset boundary không?
- Lỗi async/network có được xử lý riêng không?

## Failure Modes / Cách nó gây lỗi

- Đặt boundary quá cao làm cả page fallback dù chỉ một widget lỗi.
- Không log error nên production khó debug.
- Fallback UI gây loop hoặc crash tiếp.
- Tin error boundary bắt mọi lỗi nên bỏ qua async error handling.
- Reset boundary không rõ làm user kẹt ở fallback.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype nhỏ có thể dùng app-level fallback trước.
- Không nên đặt boundary dày đặc nếu chưa có failure domain rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Component]] vì error boundary bao quanh component subtree.
- [[React]] vì React phổ biến khái niệm Error Boundary.
- [[Logging]] vì boundary nên report error có context.
- [[Monitoring]] vì frontend crash cần quan sát production.

## Liên quan rộng

- UI resilience
- Fallback UI
- Frontend observability

## Keywords / Từ khóa tìm kiếm

- Frontend Error Boundary
- error boundary
- fallback UI
- component crash
- white screen
- frontend error reporting
- error boundary debugging

## Source trace

- React documentation
- Sentry frontend documentation
