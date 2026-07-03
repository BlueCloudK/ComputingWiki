# Programming Language

Aliases: programming language, ngôn ngữ lập trình

Type: Computer Foundation

## Context / Ngữ cảnh

Programming Language xuất hiện khi con người cần viết chỉ dẫn cho máy theo một hệ thống ký hiệu có luật rõ. Trong project, language quyết định cách code được đọc, kiểm tra, chạy, đóng gói và debug.

## Boundary / Ranh giới

### Nó là gì

Programming Language là hệ thống syntax và semantics dùng để biểu diễn computation, data, control flow, abstraction và interaction với runtime hoặc platform.

### Nó không phải là gì

Nó không phải là framework, không phải package manager, và không phải chỉ là file extension. Một language có luật behavior riêng dù cùng chạy trên một platform.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là cung cấp construct để tạo chương trình: value, expression, statement, function, module, type và control flow. Compiler/interpreter/runtime dùng các construct này để tạo behavior thực tế.

## Project Role / Vai trò trong dự án

Language choice ảnh hưởng onboarding, bug class, toolchain, deploy target, performance và cách team tổ chức abstraction. Khi đọc code, hiểu language giúp phân biệt lỗi logic với lỗi do rule của language.

## Output / Artifact nên có

- Decision note chọn language hoặc runtime
- Rule/constraint language-specific ảnh hưởng architecture
- Convention ngắn về typing, error handling, concurrency hoặc module boundary

## Decision Checklist / Câu hỏi kiểm tra

- Language này phù hợp domain và runtime target không?
- Tooling build/test/deploy có ổn với team không?
- Type/memory/concurrency model tạo lợi thế hay rủi ro gì?
- Ecosystem có đủ library ổn định cho bài toán không?
- Bug phổ biến của language này là gì?

## Failure Modes / Cách nó gây lỗi

- Chọn language theo trend nhưng không hợp deploy/runtime
- Không hiểu type hoặc memory model nên debug sai hướng
- Dùng idiom của language khác làm code khó đọc
- Đánh giá language chỉ bằng syntax mà bỏ qua tooling và runtime

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần phân tích sâu nếu project đã có language cố định và không gặp bug language-specific
- Dễ over-engineer nếu tranh luận language choice khi constraint thực tế đã rõ

## Gồm những gì

- [[Syntax]]
- [[Semantics]]
- [[Type System]]
- [[Runtime]]
- [[Memory Model]]
- [[Paradigm]]

## Nối mạnh

- [[Compiler]] vì nhiều language cần compiler để kiểm tra và chuyển đổi code
- [[Interpreter]] vì nhiều language được thực thi trực tiếp hoặc qua VM/evaluator
- [[Static Typing]] vì typing strategy thay đổi cách bắt lỗi trước khi chạy
- [[Dynamic Typing]] vì typing strategy thay đổi cách lỗi xuất hiện trong runtime

## Liên quan rộng

- Software construction
- Toolchain choice
- Developer ergonomics

## Keywords / Từ khóa tìm kiếm

- Programming Language
- ngôn ngữ lập trình
- programming
- language
- Computer Foundation
- lập trình
- ngôn ngữ

## Source trace

- Computer Foundations Map Ch09
- ACM/IEEE Computing Curricula 2020
