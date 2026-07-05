# Route Loader

Aliases: Route Loader, route data loader

Type: Frontend Framework

## Context / Ngữ cảnh

Route Loader xuất hiện khi web app cần tải dữ liệu theo route trước khi render page hoặc khi điều hướng sang route mới.

## Boundary / Ranh giới

### Nó là gì

Route Loader là hàm/cơ chế gắn với route để lấy data, validate params, redirect hoặc trả error trước khi component/page render đầy đủ.

### Nó không phải là gì

Route Loader không phải component UI. Nó nằm ở data/routing boundary và nên có contract rõ với component nhận data.

## Core Mechanism / Cơ chế lõi

Router match URL, chạy loader của route liên quan, truyền params/request/context vào loader, nhận data/redirect/error rồi render route component hoặc error boundary tương ứng.

## Project Role / Vai trò trong dự án

Dùng node này khi debug page data thiếu, loading state, redirect sai, SSR/CSR mismatch, cache invalidation hoặc route-level error handling.

## Output / Artifact nên có

- Loader input/output contract
- Route params validation
- Error/redirect behavior
- Cache/revalidation rule
- Test cho route data quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Loader chạy ở server, client hay cả hai?
- Params đã validate chưa?
- Data shape có khớp component không?
- Error/redirect được xử lý ở boundary nào?
- Revalidation xảy ra khi nào?

## Failure Modes / Cách nó gây lỗi

- Loader trả data shape khác component kỳ vọng.
- Redirect loop do auth/session logic sai.
- Loader chạy lại quá nhiều làm request dư.
- SSR và client navigation dùng data khác nhau.
- Error không được route boundary bắt nên trắng trang.

## Khi nào chưa cần hoặc dễ over-engineer

- Page static hoặc data đơn giản có thể fetch trong component trước.
- Không nên đưa business logic quá sâu vào loader nếu cần reuse ở backend/service layer.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Route]] vì loader gắn với route matching.
- [[Remix]] vì Remix dùng loader như cơ chế data chính.
- [[SSR]] vì route loader thường liên quan server rendering.
- [[Frontend Error Boundary]] vì loader error cần fallback boundary.

## Liên quan rộng

- Route data
- Redirect
- Revalidation
- Page loading

## Keywords / Từ khóa tìm kiếm

- Route Loader
- route data loader
- loader function
- route params
- data loading
- route redirect
- route loader debugging

## Source trace

- Remix documentation
- React Router documentation
