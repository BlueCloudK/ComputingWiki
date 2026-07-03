# Dependency Injection

Aliases: DI, inversion of control container, tiêm phụ thuộc

Type: Code Design / Backend

## Context / Ngữ cảnh

Dependency Injection xuất hiện khi module cần nhận dependency từ bên ngoài để giảm coupling và tăng testability.

## Boundary / Ranh giới

### Nó là gì

Dependency Injection là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Dependency Injection là constructor injection, provider/container, lifetime scope và interface boundary.

## Project Role / Vai trò trong dự án

Dependency Injection giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Dependency Injection decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Dependency Injection
- Failure note ghi rõ Dependency Injection ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Dependency Injection đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Dependency Injection không?
- Khi Dependency Injection fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Dependency Injection làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Dependency Injection nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Dependency Injection nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Dependency Injection trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Threat modeling
- Backend review

## Keywords / Từ khóa tìm kiếm

- Dependency Injection
- DI
- inversion of control container
- tiêm phụ thuộc
- dependency injection debugging
- dependency injection design
- security review
- kiểm tra bảo mật

## Source trace

- Martin Fowler DI; .NET DI docs
