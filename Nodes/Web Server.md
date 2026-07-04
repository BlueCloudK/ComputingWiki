# Web Server

Aliases: HTTP server, application server, máy chủ web

Type: Backend / Operations

## Context / Ngữ cảnh

Web Server xuất hiện khi một process hoặc service cần nhận HTTP request và trả response cho client. Nó có thể phục vụ static file, terminate TLS, reverse proxy tới upstream hoặc chạy application logic trực tiếp tùy loại server/framework.

## Boundary / Ranh giới

### Nó là gì

Web Server là thành phần lắng nghe port/network socket, parse HTTP request, quản lý connection/worker, xử lý static/dynamic response hoặc forward request tới application/upstream. Ví dụ có Nginx/Apache làm web server/reverse proxy, hoặc Node.js/Spring/Gunicorn/Kestrel làm application web server.

### Nó không phải là gì

Web Server không đồng nghĩa với toàn bộ backend. Nó chỉ là lớp nhận/gửi HTTP và điều phối request tới handler/app/upstream. Nó cũng không tự đảm bảo business logic đúng, database khỏe hoặc security đầy đủ nếu auth, validation, rate limit và error handling nằm ở layer khác.

## Core Mechanism / Cơ chế lõi

Web server bind port, accept connection, parse HTTP, xử lý TLS nếu có, áp timeout/body limit, chuyển request tới worker/handler/upstream, rồi ghi access/error log và trả response. Behavior phụ thuộc vào concurrency model như thread, event loop, worker process, connection keep-alive và request queue.

## Project Role / Vai trò trong dự án

Web Server là node cần mở khi app không listen port, request bị timeout, 502/503/504, static file sai cache, upload fail, worker hết, TLS lỗi hoặc CPU/connection tăng bất thường. Nó giúp team biết lỗi nằm ở process nhận HTTP, reverse proxy, app handler hay dependency phía sau.

## Output / Artifact nên có

- Server config: bind address, port, TLS, worker/concurrency, timeout, body size
- Route/static/proxy responsibility note: server xử lý gì, app xử lý gì
- Log/metric: request count, status code, latency, active connection, worker queue, error log
- Health check endpoint và readiness/liveness behavior nếu chạy trong container/Kubernetes
- Runbook cho port conflict, server not listening, 413, 502/503/504, TLS và worker saturation

## Decision Checklist / Câu hỏi kiểm tra

- Web server listen đúng host/port/interface chưa?
- Timeout/body size/keep-alive có phù hợp workload không?
- Concurrency model có đủ worker/thread/event loop capacity không?
- Static file/cache header/TLS terminate ở server này hay proxy phía trước?
- Access log có request id, status code và latency không?
- Health check có kiểm tra đúng readiness của app không?
- Khi server restart/deploy, connection đang mở được xử lý graceful shutdown không?

## Failure Modes / Cách nó gây lỗi

- Server không bind đúng port/interface làm load balancer/proxy không kết nối được.
- Worker/thread/event loop bão hòa làm request xếp hàng và timeout.
- Body size quá nhỏ làm upload fail với 413.
- Timeout/keep-alive sai làm connection bị cắt hoặc giữ quá lâu.
- Static cache header sai làm user nhận asset cũ sau deploy.
- Graceful shutdown thiếu làm deploy cắt request đang xử lý.
- TLS/certificate config sai làm client không thể kết nối an toàn.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype local có thể dùng dev server, nhưng production cần hiểu server thật và proxy phía trước.
- Không nên thêm nhiều lớp web server/proxy nếu chưa có nhu cầu routing/TLS/static/cache rõ.
- Không nên tuning worker/timeouts trước khi có metric về latency, active connection và queue.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Reverse Proxy]] vì nhiều web server đứng trước app như reverse proxy.
- [[Nginx]] vì Nginx là web server/reverse proxy phổ biến.
- [[HTTP]] vì web server nhận và trả HTTP request/response.
- [[Load Balancer]] vì load balancer thường gửi traffic tới web server instances.
- [[Health Check]] vì web server cần endpoint/status để orchestration biết service có sẵn sàng không.

## Liên quan rộng

- Web deployment
- Application runtime
- TLS
- Static file serving
- Operations debugging

## Keywords / Từ khóa tìm kiếm

- Web Server
- HTTP server
- application server
- máy chủ web
- listen port
- bind address
- worker process
- event loop server
- request queue
- keep alive
- TLS termination
- static file serving
- access log
- graceful shutdown
- web server debugging

## Source trace

- Nginx documentation
- Apache HTTP Server documentation
