# Runtime

Aliases: runtime environment, môi trường chạy

Type: Computer Foundation

## Context / Ngữ cảnh

Runtime xuất hiện khi code đã qua bước build/parse/check và cần môi trường thật để chạy. Nhiều bug production đến từ runtime behavior chứ không phải source code nhìn thấy ngay.

## Boundary / Ranh giới

### Nó là gì

Runtime là môi trường và service hỗ trợ chương trình khi chạy: memory management, module loading, exception handling, scheduling, standard library hooks hoặc virtual machine.

### Nó không phải là gì

Nó không phải là source code của app, không phải OS toàn bộ, và không phải build tool dù có liên hệ chặt với toolchain.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là cung cấp service mà program cần trong lúc thực thi: allocate memory, manage stack/heap, resolve symbols/modules, handle errors, schedule work hoặc bridge tới OS.

## Project Role / Vai trò trong dự án

Runtime ảnh hưởng deploy, performance, memory usage, startup time và bug chỉ xuất hiện ở môi trường thật. Hiểu runtime giúp phân biệt lỗi code, lỗi dependency và lỗi environment.

## Output / Artifact nên có

- Runtime version và constraint của project
- Note về memory/concurrency/error behavior quan trọng
- Deployment requirement cho runtime dependency

## Decision Checklist / Câu hỏi kiểm tra

- Production dùng runtime version nào?
- Runtime có garbage collection, event loop hoặc VM behavior nào cần biết không?
- Dependency/runtime nào khác giữa dev và production?
- Memory hoặc concurrency bug có đến từ runtime model không?
- Runtime có ảnh hưởng startup/performance/cost không?

## Failure Modes / Cách nó gây lỗi

- Build đúng nhưng production thiếu runtime hoặc sai version
- Memory/performance bug do không hiểu GC/event loop/thread model
- Dependency resolution khác môi trường làm behavior lệch
- Treat runtime as invisible rồi không monitor resource thực tế

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu app nhỏ chạy trong runtime chuẩn và ít issue môi trường
- Dễ over-engineer nếu tối ưu runtime trước khi đo bottleneck thật

## Gồm những gì

- [[Memory Model]]

## Nối mạnh

- [[Programming Language]] vì language behavior thường cần runtime hỗ trợ
- [[Compiler]] vì compiled code vẫn có thể phụ thuộc runtime library hoặc VM
- [[Interpreter]] vì interpreter thường chính là một phần runtime execution

## Liên quan rộng

- Operating System vì runtime dùng process, memory, file và system call của OS
- Virtual machine
- Garbage collection
- Event loop
- Production environment

## Keywords / Từ khóa tìm kiếm

- Runtime
- runtime environment
- program execution
- runtime library
- runtime error
- execution model
- môi trường chạy

## Source trace

- Computer Foundations Map Ch09
- Crafting Interpreters
