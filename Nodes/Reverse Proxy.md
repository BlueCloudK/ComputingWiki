# Reverse Proxy

Aliases: proxy ngược, HTTP reverse proxy

Type: Infrastructure / Web

## Context / Ngữ cảnh

Reverse Proxy xuất hiện khi một server đứng trước backend/app server để nhận traffic từ client rồi chuyển tiếp tới upstream phù hợp. Nó thường dùng cho TLS termination, routing theo host/path, header forwarding, buffering, compression, load balancing, access log và bảo vệ backend khỏi client traffic trực tiếp.

## Boundary / Ranh giới

### Nó là gì

Reverse Proxy là thành phần nhận request thay cho upstream server và proxy request đó vào bên trong. Client nói chuyện với proxy, còn proxy nói chuyện với app/backend. Nó có thể che topology nội bộ, chuẩn hóa request, thêm header, enforce một số policy và xử lý lỗi upstream.

### Nó không phải là gì

Reverse Proxy không phải forward proxy cho client đi internet. Nó cũng không phải application server chứa business logic chính. Nếu nhét quá nhiều routing rewrite, auth đặc biệt hoặc logic domain vào proxy, hệ thống dễ khó debug vì behavior bị chia giữa proxy config và app code.

## Core Mechanism / Cơ chế lõi

Proxy match host/path/location, chọn upstream, forward request với header/body phù hợp, rồi nhận response từ upstream để trả về client. Các yếu tố quan trọng gồm `Host`, `X-Forwarded-For`, `X-Forwarded-Proto`, TLS, buffering, timeout, body size, websocket upgrade, health check và retry/load balancing.

## Project Role / Vai trò trong dự án

Reverse Proxy là node cần mở khi deploy web app, đặt Nginx/Traefik/Envoy trước service, debug 502/504, redirect loop, mất IP thật, sai scheme HTTP/HTTPS hoặc upload/websocket fail. Nó giúp team phân biệt lỗi nằm ở browser, proxy, network hay upstream app.

## Output / Artifact nên có

- Proxy route map: domain/path → upstream service/port
- Header forwarding policy: Host, X-Forwarded-For, X-Forwarded-Proto, request id
- TLS/body-size/timeout/buffering/websocket config
- Access/error log format có upstream status và upstream response time
- Runbook cho 404 từ proxy, 413, 502, 504, redirect loop và wrong upstream

## Decision Checklist / Câu hỏi kiểm tra

- Proxy có route đúng host/path tới upstream không?
- Upstream app có nhận đúng scheme/host/client IP qua forwarded headers không?
- Timeout của proxy có khớp timeout của app và client không?
- Proxy có cần websocket/streaming/buffering config riêng không?
- Body size/upload limit có phù hợp không?
- TLS terminate ở proxy hay upstream, và app có biết request gốc là HTTPS không?
- Log có đủ để thấy upstream status, upstream latency và request id không?

## Failure Modes / Cách nó gây lỗi

- Proxy route sai làm client nhận 404/502 dù app vẫn chạy.
- Thiếu forwarded header làm app tạo redirect sai hoặc mất client IP thật.
- Proxy timeout ngắn hơn app làm client nhận 504 trong khi app vẫn xử lý.
- Buffering sai làm streaming hoặc websocket bị gián đoạn.
- Body size limit quá nhỏ làm upload fail với 413.
- TLS/scheme mismatch gây redirect loop HTTP ↔ HTTPS.
- Health check sai làm upstream khỏe bị loại khỏi pool hoặc upstream chết vẫn nhận traffic.

## Khi nào chưa cần hoặc dễ over-engineer

- Local dev hoặc app nội bộ nhỏ có thể chưa cần reverse proxy riêng nếu framework server đủ dùng.
- Không nên thêm nhiều tầng proxy nếu chưa cần routing/TLS/policy rõ, vì mỗi tầng thêm header/timeout/log cần debug.
- Nếu dùng managed load balancer/API gateway đã xử lý đủ, reverse proxy riêng có thể không cần.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Nginx]] vì Nginx là reverse proxy phổ biến trong web deployment.
- [[API Gateway]] vì gateway thường mở rộng reverse proxy bằng policy/auth/rate limit.
- [[Load Balancer]] vì reverse proxy có thể chọn upstream và phân phối traffic.
- [[Timeout]] vì proxy timeout quyết định 502/504 khi upstream chậm.
- [[Web Server]] vì reverse proxy thường đứng trước hoặc nằm trong web server layer.

## Liên quan rộng

- Web deployment
- Edge routing
- TLS termination
- Production debugging

## Keywords / Từ khóa tìm kiếm

- Reverse Proxy
- proxy ngược
- HTTP reverse proxy
- upstream
- proxy_pass
- forwarded headers
- X-Forwarded-For
- X-Forwarded-Proto
- TLS termination
- 502 bad gateway
- 504 gateway timeout
- redirect loop
- reverse proxy buffering
- websocket reverse proxy
- reverse proxy debugging

## Source trace

- Nginx documentation
- Envoy documentation
