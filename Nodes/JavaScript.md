# JavaScript

Aliases: JS, ECMAScript, ngôn ngữ JavaScript

Type: Programming Language

## Context / Ngữ cảnh

JavaScript xuất hiện khi cần viết logic chạy trên browser, Node.js hoặc tooling frontend/backend.

## Boundary / Ranh giới

### Nó là gì

JavaScript là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của JavaScript là event loop, prototype/object model, module system, package ecosystem và browser/server runtime boundary.

## Project Role / Vai trò trong dự án

JavaScript giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- JavaScript decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới JavaScript
- Failure note ghi rõ JavaScript ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- JavaScript đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của JavaScript không?
- Khi JavaScript fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của JavaScript làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên JavaScript nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu JavaScript nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh JavaScript trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Software design
- Debugging
- Operations

## Keywords / Từ khóa tìm kiếm

- JavaScript
- JS
- ECMAScript
- ngôn ngữ JavaScript
- javascript debugging
- javascript design

## Source trace

- MDN JavaScript Guide; ECMAScript specification
