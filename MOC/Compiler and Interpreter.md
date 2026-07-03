# Compiler and Interpreter

Aliases: compilers and interpreters, trình biên dịch và trình thông dịch

Type: Computer Foundation

## Context / Ngữ cảnh

Compiler and Interpreter là vùng kiến thức giúp hiểu source code được kiểm tra, chuyển đổi và thực thi như thế nào. Nó hữu ích khi debug build error, runtime behavior, language tooling hoặc performance do execution model gây ra.

## Boundary / Ranh giới

### Nó là gì

Compiler and Interpreter bao phủ hai cách chính để hiện thực một programming language: dịch code sang dạng khác trước khi chạy, hoặc đọc và thực thi code qua một runtime/evaluator.

### Nó không phải là gì

Nó không phải là hướng dẫn viết compiler đầy đủ, không đi sâu lexer/parser/AST/IR trong batch này, và không phải node riêng cho LLVM hay một toolchain cụ thể.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là biến source program thành behavior chạy được: kiểm tra rule của language, phát hiện lỗi sớm nếu có thể, chuyển code sang representation phù hợp và phối hợp với runtime khi thực thi.

## Project Role / Vai trò trong dự án

Vùng này giúp đọc lỗi build/runtime có ngữ cảnh hơn: lỗi đến từ syntax, type checking, semantic rule, runtime environment hay cách interpreter/compiler thực thi code.

## Output / Artifact nên có

- Mental model về pipeline chạy code của language đang dùng
- Note phân biệt compile-time error và runtime error
- Decision note khi chọn language/toolchain có ảnh hưởng build, deploy hoặc performance

## Decision Checklist / Câu hỏi kiểm tra

- Language/project này chạy qua compiler, interpreter hay hybrid runtime?
- Lỗi này xảy ra trước khi chạy hay trong lúc chạy?
- Representation trung gian có ảnh hưởng debug/performance không?
- Runtime dependency nào phải có trong môi trường deploy?
- Toolchain có thay đổi behavior giữa dev và production không?

## Failure Modes / Cách nó gây lỗi

- Nhầm compile-time check với runtime validation
- Build pass nhưng runtime thiếu dependency hoặc runtime version lệch
- Tối ưu performance sai tầng vì không hiểu code được thực thi thế nào
- Treat interpreted language như không có compile/check phase nào cả

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu chỉ cần dùng toolchain chuẩn và lỗi đã rõ
- Dễ over-engineer nếu tạo nhiều node compiler internals trước khi có nhu cầu đọc/debug

## Gồm những gì

- [[Compiler]]
- [[Interpreter]]

## Nối mạnh

- [[Programming Language]] vì compiler/interpreter hiện thực luật và behavior của language
- [[Runtime]] vì nhiều language phối hợp compile/interpret với runtime services
- [[Syntax]] vì source code phải được parse theo syntax trước khi kiểm tra sâu hơn
- [[Semantics]] vì compiler/interpreter phải giữ đúng nghĩa của chương trình

## Liên quan rộng

- Build tooling
- Language implementation
- Runtime performance
- Developer diagnostics

## Source trace

- Computer Foundations Map Ch09
- Crafting Interpreters
- Engineering a Compiler
