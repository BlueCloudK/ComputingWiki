# Traefik

Aliases: Traefik, Traefik proxy, cloud native reverse proxy

Type: Infrastructure / Reverse Proxy

## Context / Ngữ cảnh

Traefik là reverse proxy/load balancer cloud-native thường dùng với Docker, Kubernetes và dynamic service discovery.

## Boundary / Ranh giới

### Nó là gì

Nó định tuyến HTTP/TCP traffic tới service qua router, middleware, service definition và provider như Docker/Kubernetes.

### Nó không phải là gì

Nó không thay thế application auth, API gateway policy đầy đủ hoặc network security group/firewall.

## Core Mechanism / Cơ chế lõi

Traefik đọc config từ provider, tạo router theo host/path/rule, áp middleware rồi forward traffic tới backend service.

## Project Role / Vai trò trong dự án

Node này giúp debug ingress routing, TLS certificate, service discovery, middleware redirect/auth và local/prod container routing.

## Output / Artifact nên có

- Router/service/middleware config
- TLS certificate resolver config
- Route test cho host/path quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Host/path rule có match đúng service không?
- TLS certificate có tự renew và đúng domain không?
- Middleware redirect/auth/header có chạy đúng thứ tự không?
- Provider label/annotation có drift so với service thật không?

## Failure Modes / Cách nó gây lỗi

- Rule match sai làm traffic vào nhầm service
- Cert resolver lỗi làm HTTPS fail khi hết hạn
- Middleware redirect loop làm client không vào được app

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Traefik nếu một reverse proxy tĩnh đơn giản đã đủ
- Dễ over-engineer nếu dùng dynamic routing phức tạp cho vài service ít thay đổi

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Reverse Proxy]] vì Traefik là reverse proxy/load balancer
- [[TLS]] vì Traefik thường quản lý HTTPS certificate ở edge

## Liên quan rộng

- Container deployment
- Kubernetes ingress
- Edge routing

## Keywords / Từ khóa tìm kiếm

- Traefik
- Traefik proxy
- reverse proxy
- ingress routing
- router middleware service
- TLS certificate resolver
- Docker labels
- Kubernetes ingress

## Source trace

- Traefik official documentation
