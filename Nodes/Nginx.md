# Nginx

Aliases: nginx web server, nginx reverse proxy

Type: Infrastructure / Web

## Context / Ngữ cảnh

Nginx xuất hiện khi hệ thống cần web server hoặc reverse proxy để phục vụ static file, terminate TLS, route request tới upstream, cân bằng tải hoặc làm edge layer trước app server. Nó thường nằm giữa browser/client và backend service.

## Boundary / Ranh giới

### Nó là gì

Nginx là web server/reverse proxy cấu hình bằng server block, location, upstream và directive. Nó có thể xử lý TLS, static files, proxy headers, buffering, compression, client body limit, timeout và load balancing cơ bản.

### Nó không phải là gì

Nginx không phải application server chứa business logic chính. Nó cũng không tự hiểu domain rule của backend. Nếu dùng Nginx để nhét quá nhiều logic rewrite/routing đặc biệt, hệ thống dễ khó debug vì behavior bị chia giữa config proxy và code app.

## Core Mechanism / Cơ chế lõi

Nginx nhận request, match `server_name` và `location`, rồi quyết định serve file, return response hoặc proxy tới upstream. Khi proxy, các header như `Host`, `X-Forwarded-For`, `X-Forwarded-Proto`, timeout, buffering và body size quyết định backend thấy request như thế nào và client nhận lỗi gì khi upstream chậm/hỏng.

## Project Role / Vai trò trong dự án

Nginx ảnh hưởng trực tiếp tới deploy web app, HTTPS, reverse proxy, static asset, upload limit, websocket/proxy behavior và lỗi 502/504. Khi debug production, team cần biết request fail ở Nginx, network, upstream app hay browser cache/header layer.

## Output / Artifact nên có

- Nginx config: server block, location, upstream, TLS, proxy headers
- Route/proxy map: domain/path nào tới service nào
- Timeout/body-size/buffering decision note cho API, upload, websocket hoặc streaming
- Access log/error log format có request id hoặc upstream timing nếu cần
- Runbook cho 404, 413, 502, 504, redirect loop và wrong upstream header

## Decision Checklist / Câu hỏi kiểm tra

- `server_name` và `location` có match đúng domain/path không?
- Nginx có forward đúng `Host`, `X-Forwarded-For` và `X-Forwarded-Proto` không?
- Timeout của Nginx có khớp timeout của app/upstream không?
- `client_max_body_size` có phù hợp upload limit không?
- Static file/cache header có làm user nhận asset cũ không?
- Websocket/streaming có cần cấu hình upgrade/buffering riêng không?
- Log có đủ để biết upstream status và upstream response time không?

## Failure Modes / Cách nó gây lỗi

- Location rule sai làm request bị route nhầm hoặc trả 404 từ Nginx thay vì app.
- Thiếu proxy header làm backend tạo URL sai, redirect loop hoặc mất IP thật.
- Upstream app down/chậm làm Nginx trả 502/504.
- Body size quá nhỏ làm upload fail với 413.
- Buffering/timeout sai làm streaming hoặc websocket bị cắt.
- TLS/certificate/server_name sai làm client không vào được đúng site.

## Khi nào chưa cần hoặc dễ over-engineer

- Local dev hoặc app nhỏ có thể dùng dev server/reverse proxy đơn giản trước.
- Không nên cấu hình rewrite/proxy quá phức tạp nếu routing có thể rõ hơn ở app hoặc gateway.
- Nếu dùng managed platform/load balancer đã xử lý TLS/routing, Nginx có thể không cần trong app layer.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Reverse Proxy]] vì Nginx thường được dùng như reverse proxy trước backend.
- [[Load Balancer]] vì Nginx có thể phân phối request tới nhiều upstream.
- [[API Gateway]] vì Nginx có thể làm edge proxy hoặc nền cho gateway behavior đơn giản.
- [[Timeout]] vì proxy timeout quyết định lỗi 504 và behavior khi upstream chậm.

## Liên quan rộng

- Web deployment
- TLS termination
- Static file serving
- Production debugging

## Keywords / Từ khóa tìm kiếm

- Nginx
- nginx web server
- nginx reverse proxy
- server block
- location block
- upstream
- proxy_pass
- proxy headers
- X-Forwarded-For
- X-Forwarded-Proto
- 502 bad gateway
- 504 gateway timeout
- client_max_body_size
- nginx config
- nginx debugging

## Source trace

- Nginx documentation
