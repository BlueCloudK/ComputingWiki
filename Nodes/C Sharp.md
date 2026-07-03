# C Sharp

Aliases: C#, CSharp, ngôn ngữ C#

Type: Programming Language

## Context / Ngữ cảnh

C Sharp xuất hiện khi xây backend .NET, desktop app, game dev hoặc enterprise application.

## Boundary / Ranh giới

### Nó là gì

C Sharp là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của C Sharp là static typing, CLR runtime, async model, managed memory và .NET libraries.

## Project Role / Vai trò trong dự án

C Sharp giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- C Sharp decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới C Sharp
- Failure note ghi rõ C Sharp ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- C Sharp đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của C Sharp không?
- Khi C Sharp fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của C Sharp làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên C Sharp nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu C Sharp nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh C Sharp trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Software design
- Debugging
- Operations

## Keywords / Từ khóa tìm kiếm

- C Sharp
- C#
- CSharp
- ngôn ngữ C#
- c sharp debugging
- c sharp design

## Source trace

- Microsoft C# documentation
