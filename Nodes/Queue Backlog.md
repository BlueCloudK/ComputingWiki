# Queue Backlog

Aliases: queue buildup, hàng đợi tồn đọng

Type: Failure Pattern

## Context / Ngữ cảnh

Queue Backlog xuất hiện khi queue tích lũy nhanh hơn tốc độ consumer xử lý, làm tăng latency và memory pressure.

## Boundary / Ranh giới

### Nó là gì

Queue Backlog là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Queue Backlog là arrival rate, service rate, queue length, consumer lag và backpressure.

## Project Role / Vai trò trong dự án

Queue Backlog giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Queue Backlog decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Queue Backlog
- Failure note ghi rõ Queue Backlog ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Queue Backlog đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Queue Backlog không?
- Khi Queue Backlog fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Queue Backlog làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Queue Backlog nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Queue Backlog nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Queue Backlog trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Queue Backlog
- queue buildup
- hàng đợi tồn đọng
- queue backlog debugging
- queue backlog design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Little Law; Kafka docs
