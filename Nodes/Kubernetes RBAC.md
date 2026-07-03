# Kubernetes RBAC

Aliases: RBAC Kubernetes, role based access control

Type: Kubernetes / Security

## Context / Ngữ cảnh

Kubernetes RBAC xuất hiện khi cluster cần phân quyền Kubernetes theo role và subject.

## Boundary / Ranh giới

### Nó là gì

Kubernetes RBAC là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Kubernetes RBAC là Role, ClusterRole, RoleBinding, ServiceAccount và least privilege.

## Project Role / Vai trò trong dự án

Kubernetes RBAC giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Kubernetes RBAC decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Kubernetes RBAC
- Failure note ghi rõ Kubernetes RBAC ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Kubernetes RBAC đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Kubernetes RBAC không?
- Khi Kubernetes RBAC fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Kubernetes RBAC làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Kubernetes RBAC nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Kubernetes RBAC nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Kubernetes RBAC trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Threat modeling
- Backend review
- Platform engineering
- Deployment operations
- Production reliability

## Keywords / Từ khóa tìm kiếm

- Kubernetes RBAC
- RBAC Kubernetes
- role based access control
- kubernetes rbac debugging
- kubernetes rbac design
- security review
- kiểm tra bảo mật
- deployment config
- vận hành hạ tầng

## Source trace

- Kubernetes RBAC docs
