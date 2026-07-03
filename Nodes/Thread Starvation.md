# Thread Starvation

Aliases: thread pool starvation, thiếu thread xử lý

Type: Failure Pattern

## Context / Ngữ cảnh

Thread Starvation xuất hiện khi thread pool bị block hoặc chiếm hết làm request mới không được xử lý kịp.

## Boundary / Ranh giới

### Nó là gì

Thread Starvation là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Thread Starvation là blocking call, worker pool, queue wait, async boundary và saturation.

## Project Role / Vai trò trong dự án

Thread Starvation giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Thread Starvation decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Thread Starvation
- Failure note ghi rõ Thread Starvation ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Thread Starvation đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Thread Starvation không?
- Khi Thread Starvation fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Thread Starvation làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Thread Starvation nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Thread Starvation nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Thread Starvation trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Thread Starvation
- thread pool starvation
- thiếu thread xử lý
- thread starvation debugging
- thread starvation design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- .NET ThreadPool docs; Java concurrency docs
