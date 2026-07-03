# Stale Cache

Aliases: stale cached data, cache cũ

Type: Failure Pattern

## Context / Ngữ cảnh

Stale Cache xuất hiện khi dữ liệu cache đã lỗi thời nhưng vẫn được trả về do invalidation hoặc TTL không phù hợp.

## Boundary / Ranh giới

### Nó là gì

Stale Cache là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Stale Cache là TTL, invalidation, write-through/write-back, versioning và consistency boundary.

## Project Role / Vai trò trong dự án

Stale Cache giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Stale Cache decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Stale Cache
- Failure note ghi rõ Stale Cache ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Stale Cache đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Stale Cache không?
- Khi Stale Cache fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Stale Cache làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Stale Cache nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Stale Cache nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Stale Cache trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Stale Cache
- stale cached data
- cache cũ
- stale cache debugging
- stale cache design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Designing Data-Intensive Applications; caching docs
