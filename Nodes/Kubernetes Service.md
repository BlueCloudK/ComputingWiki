# Kubernetes Service

Aliases: Service, K8s service

Type: Kubernetes

## Context / Ngữ cảnh

Kubernetes Service xuất hiện khi nhóm Pod cần endpoint ổn định qua virtual IP hoặc DNS.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Service là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Kubernetes Service là selector, endpoint, ClusterIP, NodePort, LoadBalancer và service discovery.

## Project Role / Vai trò trong dự án

Kubernetes Service giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Kubernetes Service decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Kubernetes Service
- Failure note ghi rõ Kubernetes Service ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Kubernetes Service đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Kubernetes Service không?
- Khi Kubernetes Service fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Kubernetes Service làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Kubernetes Service nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Kubernetes Service nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Kubernetes Service trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability

## Keywords / Từ khóa tìm kiếm

- Kubernetes Service
- Service
- K8s service
- kubernetes service debugging
- kubernetes service design
- deployment config
- vận hành hạ tầng

## Source trace

- Kubernetes docs
