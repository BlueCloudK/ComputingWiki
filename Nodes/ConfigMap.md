# ConfigMap

Aliases: Kubernetes ConfigMap, config map

Type: Kubernetes

## Context / Ngữ cảnh

ConfigMap xuất hiện khi Pod cần nhận cấu hình không nhạy cảm qua env hoặc file.

## Boundary / Ranh giới

### Nó là gì

ConfigMap là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của ConfigMap là key-value config, volume mount, envFrom và rollout behavior khi config đổi.

## Project Role / Vai trò trong dự án

ConfigMap giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- ConfigMap decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới ConfigMap
- Failure note ghi rõ ConfigMap ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- ConfigMap đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của ConfigMap không?
- Khi ConfigMap fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của ConfigMap làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên ConfigMap nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu ConfigMap nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh ConfigMap trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability

## Keywords / Từ khóa tìm kiếm

- ConfigMap
- Kubernetes ConfigMap
- config map
- configmap debugging
- configmap design
- deployment config
- vận hành hạ tầng

## Source trace

- Kubernetes docs
