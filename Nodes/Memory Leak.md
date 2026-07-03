# Memory Leak

Aliases: leak bộ nhớ, rò rỉ bộ nhớ

Type: Failure Pattern

## Context / Ngữ cảnh

Memory Leak xuất hiện khi object, buffer hoặc reference vẫn bị giữ sau khi không còn cần.

## Boundary / Ranh giới

### Nó là gì

Memory Leak là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Memory Leak là heap growth, reference retention, cache leak, listener leak và profiling.

## Project Role / Vai trò trong dự án

Memory Leak giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Memory Leak decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Memory Leak
- Failure note ghi rõ Memory Leak ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Memory Leak đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Memory Leak không?
- Khi Memory Leak fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Memory Leak làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Memory Leak nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Memory Leak nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Memory Leak trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- Memory Leak
- leak bộ nhớ
- rò rỉ bộ nhớ
- memory leak debugging
- memory leak design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Java memory management docs; Chrome memory profiling docs
