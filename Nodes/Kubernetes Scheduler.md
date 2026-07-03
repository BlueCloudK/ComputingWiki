# Kubernetes Scheduler

Aliases: kube-scheduler, scheduler Kubernetes

Type: Kubernetes

## Context / Ngữ cảnh

Kubernetes Scheduler xuất hiện khi Pod mới cần được đặt lên node phù hợp theo resource và policy.

## Boundary / Ranh giới

### Nó là gì

Kubernetes Scheduler là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Kubernetes Scheduler là filter, score, affinity, taint/toleration và resource request.

## Project Role / Vai trò trong dự án

Kubernetes Scheduler giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Kubernetes Scheduler decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Kubernetes Scheduler
- Failure note ghi rõ Kubernetes Scheduler ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Kubernetes Scheduler đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Kubernetes Scheduler không?
- Khi Kubernetes Scheduler fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Kubernetes Scheduler làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Kubernetes Scheduler nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Kubernetes Scheduler nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Kubernetes Scheduler trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability

## Keywords / Từ khóa tìm kiếm

- Kubernetes Scheduler
- kube-scheduler
- scheduler Kubernetes
- kubernetes scheduler debugging
- kubernetes scheduler design
- deployment config
- vận hành hạ tầng

## Source trace

- Kubernetes docs
