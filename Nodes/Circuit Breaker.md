# Circuit Breaker

Aliases: circuit breaker pattern, ngắt mạch lỗi

Type: Failure Pattern

## Context / Ngữ cảnh

Circuit Breaker xuất hiện khi dependency đang lỗi cần được ngừng gọi tạm thời để tránh cascade và cho hệ thống phục hồi.

## Boundary / Ranh giới

### Nó là gì

Circuit Breaker là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Circuit Breaker là closed/open/half-open state, failure threshold, cooldown và fallback.

## Project Role / Vai trò trong dự án

Circuit Breaker giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Circuit Breaker decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Circuit Breaker
- Failure note ghi rõ Circuit Breaker ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Circuit Breaker đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Circuit Breaker không?
- Khi Circuit Breaker fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Circuit Breaker làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Circuit Breaker nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Circuit Breaker nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Circuit Breaker trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Circuit Breaker
- circuit breaker pattern
- ngắt mạch lỗi
- circuit breaker debugging
- circuit breaker design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Release It!; Microsoft Architecture Patterns
