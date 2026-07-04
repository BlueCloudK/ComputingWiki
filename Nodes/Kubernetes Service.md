# Kubernetes Service

Aliases: Service, K8s service

Type: Kubernetes

## Context / Ngữ cảnh

Kubernetes Service xuất hiện khi một nhóm Pod cần endpoint ổn định dù Pod có thể bị tạo lại, đổi IP hoặc scale lên/xuống. Nó là lớp network abstraction giúp workload khác gọi app bằng DNS/service name thay vì gọi trực tiếp Pod IP.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Service là resource tạo stable virtual endpoint cho các Pod được chọn bằng label selector. Service có thể là ClusterIP, NodePort, LoadBalancer hoặc ExternalName, và map `port` của service tới `targetPort` của container/Pod.

### Nó không phải là gì

Kubernetes Service không tự tạo Pod và không đảm bảo Pod healthy nếu selector chọn sai. Nó cũng không phải Ingress/API Gateway, dù LoadBalancer service có thể expose traffic ra ngoài. Service chỉ route tới endpoint phù hợp; app-level routing, auth và business logic vẫn nằm ở layer khác.

## Core Mechanism / Cơ chế lõi

Service dùng selector để tìm Pod matching labels, tạo endpoint/EndpointSlice, rồi cluster DNS cho phép gọi bằng tên service. Khi client gọi Service IP/DNS, kube-proxy hoặc dataplane route traffic tới một endpoint Pod phù hợp. Nếu selector, port hoặc targetPort sai, Service tồn tại nhưng không route được traffic đúng.

## Project Role / Vai trò trong dự án

Kubernetes Service ảnh hưởng trực tiếp tới service discovery, internal networking và expose app trong cluster. Khi debug lỗi “app chạy nhưng không gọi được”, team phải kiểm tra selector, endpoints, port mapping, DNS, readiness và service type trước khi đổ lỗi cho app code.

## Output / Artifact nên có

- Service manifest: type, selector, ports, targetPort, protocol
- Label contract giữa Deployment/Pod và Service selector
- DNS/service discovery note cho client trong cluster
- Debug checklist: service, endpoints, pod labels, readiness, port-forward/curl test
- Exposure decision: ClusterIP, NodePort, LoadBalancer hay Ingress/Gateway

## Decision Checklist / Câu hỏi kiểm tra

- Selector của Service có match label Pod thật không?
- Service `port` và Pod `targetPort` có đúng không?
- Pod có Ready không, và endpoint có được tạo không?
- Service type có phù hợp: internal ClusterIP hay external LoadBalancer?
- Client gọi đúng DNS name/namespace chưa?
- NetworkPolicy hoặc firewall có chặn traffic không?
- Có cần Ingress/API Gateway thay vì expose trực tiếp bằng LoadBalancer không?

## Failure Modes / Cách nó gây lỗi

- Selector sai làm Service không có endpoint dù Pod vẫn chạy.
- `targetPort` sai làm connection fail hoặc route tới port không có app lắng nghe.
- Pod chưa Ready nên endpoint không nhận traffic, gây service không route như mong đợi.
- Service name/namespace sai làm DNS resolve fail.
- LoadBalancer service không provision external IP do cloud/provider config sai.
- Expose service sai type làm app private bị public hoặc public app không truy cập được.

## Khi nào chưa cần hoặc dễ over-engineer

- Pod/job chạy một lần không cần endpoint ổn định có thể không cần Service.
- Không nên dùng LoadBalancer cho mọi service nội bộ; ClusterIP + Ingress/Gateway thường rõ hơn.
- Không nên dùng Service để giải quyết routing phức tạp theo path/header; đó là vai trò của Ingress/Gateway/API layer.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes]] vì Service là networking abstraction cơ bản của Kubernetes.
- [[Pod]] vì Service route traffic tới Pod matching selector.
- [[Load Balancer]] vì Service type LoadBalancer expose endpoint qua load balancer bên ngoài.
- [[Kubernetes Controller]] vì controller duy trì endpoint/EndpointSlice liên quan tới Service.

## Liên quan rộng

- Service discovery
- Cluster networking
- Internal API communication
- Ingress and gateway design

## Keywords / Từ khóa tìm kiếm

- Kubernetes Service
- Service
- K8s service
- ClusterIP
- NodePort
- LoadBalancer service
- ExternalName
- service selector
- EndpointSlice
- Kubernetes DNS
- targetPort
- service port
- no endpoints
- service discovery
- kubernetes service debugging

## Source trace

- Kubernetes Service documentation
