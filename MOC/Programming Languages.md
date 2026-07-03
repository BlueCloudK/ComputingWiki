# Programming Languages

Aliases: programming language theory, ngôn ngữ lập trình

Type: Computer Foundation

## Context / Ngữ cảnh

Programming Languages là vùng kiến thức giúp hiểu code được biểu diễn, kiểm tra, chạy và giới hạn bởi ngôn ngữ như thế nào. Nó quan trọng khi đọc code lạ, debug runtime behavior, hoặc chọn language cho một hệ thống.

## Boundary / Ranh giới

### Nó là gì

Programming Languages bao phủ syntax, semantics, type system, runtime, memory model và paradigm. Nó giải thích luật của ngôn ngữ trước khi code đi vào compiler, interpreter hoặc runtime.

### Nó không phải là gì

Nó không phải là tutorial học một language cụ thể, không phải style guide, và không phải danh sách framework/tool của một ecosystem.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là mapping từ text/source code sang behavior: code có grammar nào, name/type được kiểm tra ra sao, statement/expression có nghĩa gì, runtime quản lý state/memory thế nào.

## Project Role / Vai trò trong dự án

Vùng này giúp dev hiểu vì sao cùng một ý tưởng nhưng behavior khác nhau giữa language: typing, nullability, mutability, concurrency, memory ownership hoặc runtime exception.

## Output / Artifact nên có

- Note chọn language hoặc runtime cho project
- Rule về type, memory hoặc concurrency ảnh hưởng design
- Checklist bug language-specific khi debug

## Decision Checklist / Câu hỏi kiểm tra

- Language này kiểm tra lỗi ở compile-time hay runtime?
- Runtime có quản lý memory, concurrency hoặc module loading theo cách đặc biệt không?
- Paradigm chính có hợp với domain và team không?
- Type system có giúp bắt bug thật hay làm design phức tạp hơn?
- Behavior nào phụ thuộc vào implementation/runtime chứ không chỉ syntax?

## Failure Modes / Cách nó gây lỗi

- Nhầm syntax đẹp với semantic rõ
- Chọn language theo sở thích nhưng bỏ qua runtime/deployment constraint
- Debug sai vì không hiểu static/dynamic typing hoặc memory model
- Viết code theo paradigm trái ngược với idiom của language

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu chỉ dùng language quen thuộc cho CRUD nhỏ
- Dễ over-engineer nếu biến mọi khác biệt syntax thành tranh luận theory

## Gồm những gì

- [[Programming Language]]
- [[Type System]]
- [[Syntax]]
- [[Semantics]]
- [[Runtime]]
- [[Memory Model]]
- [[Paradigm]]
- [[Static Typing]]
- [[Dynamic Typing]]

## Nối mạnh

- [[Compiler and Interpreter]] vì compiler/interpreter là cách language được kiểm tra và thực thi
- [[Operating System]] vì runtime cuối cùng vẫn chạy trên process, memory, file và system call
- [[Software Engineering]] vì language choice ảnh hưởng maintainability, tooling và delivery

## Liên quan rộng

- Language design
- Runtime debugging
- Developer productivity
- Software construction

## Keywords / Từ khóa tìm kiếm

- Programming Languages
- Programming Languages MOC
- programming languages map
- mục lục kiến thức
- nhánh kiến thức
- programming language theory
- ngôn ngữ lập trình
- language design
- runtime behavior
- type checking
- debug runtime
- Programming Language
- Type System
- Syntax
- Semantics

## Source trace

- Computer Foundations Map Ch09
- ACM/IEEE Computing Curricula 2020
- Types and Programming Languages
