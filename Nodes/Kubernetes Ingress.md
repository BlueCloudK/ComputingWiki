# Kubernetes Ingress

Aliases: Ingress, K8s ingress

Type: Kubernetes

## Context / Ngữ cảnh

Kubernetes Ingress xuất hiện khi HTTP/HTTPS từ ngoài cluster cần được định tuyến vào service bên trong.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Ingress là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Kubernetes Ingress là host rule, path rule, ingress controller, TLS secret và annotation.

## Project Role / Vai trò trong dự án

Kubernetes Ingress giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Kubernetes Ingress decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Kubernetes Ingress
- Failure note ghi rõ Kubernetes Ingress ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Kubernetes Ingress đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Kubernetes Ingress không?
- Khi Kubernetes Ingress fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Kubernetes Ingress làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Kubernetes Ingress nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Kubernetes Ingress nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Kubernetes Ingress trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability

## Keywords / Từ khóa tìm kiếm

- Kubernetes Ingress
- Ingress
- K8s ingress
- kubernetes ingress debugging
- kubernetes ingress design
- deployment config
- vận hành hạ tầng

## Source trace

- Kubernetes docs
