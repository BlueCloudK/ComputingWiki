# C Plus Plus

Aliases: C++, CPP, ngôn ngữ C++

Type: Programming Language

## Context / Ngữ cảnh

C Plus Plus xuất hiện khi cần application/system hiệu năng cao với kiểm soát resource sâu.

## Boundary / Ranh giới

### Nó là gì

C Plus Plus là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của C Plus Plus là value semantics, RAII, template, object lifetime và compilation model.

## Project Role / Vai trò trong dự án

C Plus Plus giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- C Plus Plus decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới C Plus Plus
- Failure note ghi rõ C Plus Plus ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- C Plus Plus đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của C Plus Plus không?
- Khi C Plus Plus fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của C Plus Plus làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên C Plus Plus nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu C Plus Plus nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh C Plus Plus trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Software design
- Debugging
- Operations

## Keywords / Từ khóa tìm kiếm

- C Plus Plus
- C++
- CPP
- ngôn ngữ C++
- c plus plus debugging
- c plus plus design

## Source trace

- C++ reference; ISO C++ standard
