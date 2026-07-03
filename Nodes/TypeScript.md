# TypeScript

Aliases: TS, typed JavaScript, JavaScript có kiểu

Type: Programming Language

## Context / Ngữ cảnh

TypeScript xuất hiện khi code JavaScript bắt đầu lớn và cần kiểm tra contract trước runtime.

## Boundary / Ranh giới

### Nó là gì

TypeScript là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của TypeScript là type annotation, structural typing, compiler check và emit JavaScript cho runtime thật.

## Project Role / Vai trò trong dự án

TypeScript giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- TypeScript decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới TypeScript
- Failure note ghi rõ TypeScript ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- TypeScript đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của TypeScript không?
- Khi TypeScript fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của TypeScript làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên TypeScript nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu TypeScript nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh TypeScript trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Software design
- Debugging
- Operations

## Keywords / Từ khóa tìm kiếm

- TypeScript
- TS
- typed JavaScript
- JavaScript có kiểu
- typescript debugging
- typescript design

## Source trace

- TypeScript Handbook
