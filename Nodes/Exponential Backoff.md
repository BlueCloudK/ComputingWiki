# Exponential Backoff

Aliases: backoff, exponential retry delay, giãn cách retry

Type: Failure Pattern

## Context / Ngữ cảnh

Exponential Backoff xuất hiện khi nhiều retry cần giãn ra để không dồn tải lên dependency đang lỗi.

## Boundary / Ranh giới

### Nó là gì

Exponential Backoff là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Exponential Backoff là base delay, multiplier, jitter, max delay và retry cap.

## Project Role / Vai trò trong dự án

Exponential Backoff giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Exponential Backoff decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Exponential Backoff
- Failure note ghi rõ Exponential Backoff ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Exponential Backoff đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Exponential Backoff không?
- Khi Exponential Backoff fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Exponential Backoff làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Exponential Backoff nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Exponential Backoff nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Exponential Backoff trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Exponential Backoff
- backoff
- exponential retry delay
- giãn cách retry
- exponential backoff debugging
- exponential backoff design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- AWS Builders Library; Google SRE Book
