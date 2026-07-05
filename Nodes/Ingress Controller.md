# Ingress Controller

Aliases: Ingress Controller, ingress controller

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Ingress Controller xuất hiện trong Kubernetes khi cần đưa traffic HTTP/HTTPS từ bên ngoài cluster vào các service bên trong.

## Boundary / Ranh giới

### Nó là gì

Ingress Controller là component thực thi rule Ingress. Nó đọc Ingress resource rồi cấu hình proxy/load balancer để route traffic theo host, path, TLS và annotation.

### Nó không phải là gì

Ingress Controller không phải bản thân Ingress resource. Ingress là config; controller là phần chạy thật để áp config đó.

## Core Mechanism / Cơ chế lõi

Controller watch Kubernetes API, thấy Ingress/Service/Endpoint thay đổi thì cập nhật proxy config. Request bên ngoài đi vào controller, được match host/path rồi forward tới service backend.

## Project Role / Vai trò trong dự án

Dùng node này khi debug route 404/502, TLS lỗi, host/path không match, annotation sai hoặc traffic không vào đúng service trong Kubernetes.

## Output / Artifact nên có

- Ingress resource
- Controller class/config
- TLS secret note
- Host/path routing table
- Backend service mapping

## Decision Checklist / Câu hỏi kiểm tra

- Ingress class có khớp controller không?
- Host/path rule có match request thật không?
- TLS secret có đúng namespace không?
- Backend service/port có tồn tại không?
- Controller log báo lỗi gì?

## Failure Modes / Cách nó gây lỗi

- Ingress class sai nên controller bỏ qua rule.
- Service port sai gây 502/503.
- TLS secret thiếu làm HTTPS fail.
- Path rewrite/annotation sai làm route lệch.
- Controller thiếu permission hoặc chưa chạy.

## Khi nào chưa cần hoặc dễ over-engineer

- Service nội bộ không cần public HTTP route thì chưa cần Ingress.
- Cluster nhỏ có thể dùng LoadBalancer service trực tiếp trước.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes Service]] vì Ingress route traffic tới Service backend.
- [[Kubernetes RBAC]] vì controller cần permission watch resource.
- [[TLS]] vì Ingress thường terminate HTTPS.
- [[Reverse Proxy]] vì controller thường cấu hình reverse proxy.

## Liên quan rộng

- Kubernetes networking
- HTTP routing
- Edge traffic

## Keywords / Từ khóa tìm kiếm

- Ingress Controller
- Kubernetes Ingress
- ingress class
- host path routing
- TLS secret
- ingress 502
- ingress controller debugging

## Source trace

- Kubernetes official docs
- NGINX Ingress Controller documentation
