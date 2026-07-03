# Retry Storm

Aliases: retry amplification, bão retry

Type: Failure Pattern

## Context / Ngữ cảnh

Retry Storm xuất hiện khi nhiều client retry đồng thời làm dependency càng quá tải và lâu hồi phục hơn.

## Boundary / Ranh giới

### Nó là gì

Retry Storm là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Retry Storm là synchronized retry, missing backoff, timeout mismatch và cascading failure.

## Project Role / Vai trò trong dự án

Retry Storm giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Retry Storm decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Retry Storm
- Failure note ghi rõ Retry Storm ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Retry Storm đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Retry Storm không?
- Khi Retry Storm fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Retry Storm làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Retry Storm nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Retry Storm nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Retry Storm trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Retry Storm
- retry amplification
- bão retry
- retry storm debugging
- retry storm design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Google SRE Book; AWS Builders Library
