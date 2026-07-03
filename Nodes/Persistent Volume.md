# Persistent Volume

Aliases: PV, Kubernetes persistent volume

Type: Kubernetes / Storage

## Context / Ngữ cảnh

Persistent Volume xuất hiện khi Pod cần storage bền vững không mất theo vòng đời container.

## Boundary / Ranh giới

### Nó là gì

Persistent Volume là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Persistent Volume là PV, PVC, storage class, access mode, reclaim policy và volume binding.

## Project Role / Vai trò trong dự án

Persistent Volume giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Persistent Volume decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Persistent Volume
- Failure note ghi rõ Persistent Volume ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Persistent Volume đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Persistent Volume không?
- Khi Persistent Volume fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Persistent Volume làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Persistent Volume nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Persistent Volume nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Persistent Volume trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability
- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Persistent Volume
- PV
- Kubernetes persistent volume
- persistent volume debugging
- persistent volume design
- deployment config
- vận hành hạ tầng
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Kubernetes docs
