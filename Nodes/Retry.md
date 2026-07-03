# Retry

Aliases: retry logic, thử lại request, retry operation

Type: Failure Pattern

## Context / Ngữ cảnh

Retry xuất hiện khi operation thất bại tạm thời và có thể thử lại mà không làm sai dữ liệu.

## Boundary / Ranh giới

### Nó là gì

Retry là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Retry là retry condition, max attempt, backoff, idempotency và retry budget.

## Project Role / Vai trò trong dự án

Retry giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Retry decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Retry
- Failure note ghi rõ Retry ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Retry đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Retry không?
- Khi Retry fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Retry làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Retry nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Retry nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Retry trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Retry
- retry logic
- thử lại request
- retry operation
- retry debugging
- retry design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Google SRE Book; AWS Builders Library
