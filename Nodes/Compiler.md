# Compiler

Aliases: compiler, trình biên dịch

Type: Computer Foundation

## Context / Ngữ cảnh

Compiler xuất hiện khi source code cần được kiểm tra và chuyển sang representation khác trước khi chạy, như machine code, bytecode hoặc một language/runtime target khác.

## Boundary / Ranh giới

### Nó là gì

Compiler là chương trình dịch source program sang target representation trong khi cố giữ nguyên semantics và phát hiện lỗi càng sớm càng tốt.

### Nó không phải là gì

Nó không phải là interpreter, không phải build system toàn bộ, và trong batch này không đi sâu lexer/parser/AST/IR/codegen.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là analysis và translation: đọc code theo syntax, kiểm tra type/semantic rule, tối ưu nếu cần và sinh output để runtime/machine thực thi.

## Project Role / Vai trò trong dự án

Compiler ảnh hưởng feedback loop, build time, error diagnostics, performance và portability. Hiểu compiler giúp đọc lỗi build tốt hơn và biết bug xảy ra trước hay sau khi program bắt đầu chạy.

## Output / Artifact nên có

- Build artifact hoặc compiled output
- Compile-time diagnostics
- Compiler/toolchain version dùng trong project

## Decision Checklist / Câu hỏi kiểm tra

- Compiler đang target machine code, bytecode hay language khác?
- Lỗi này là syntax, type, semantic hay toolchain config?
- Compiler version khác nhau có tạo output/diagnostic khác không?
- Optimization có làm debug/performance thay đổi không?
- Runtime dependency nào vẫn cần dù code đã compile?

## Failure Modes / Cách nó gây lỗi

- Nhầm compiler error với runtime behavior
- Build pass ở máy dev nhưng fail CI vì toolchain/version lệch
- Optimization hoặc transpilation làm stack trace/debug khó đọc
- Tin compiled output nhanh hơn mà không đo bottleneck thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần compiler internals nếu chỉ cần fix build config đơn giản
- Dễ over-engineer nếu tạo deep compiler pipeline trước khi có nhu cầu học/debug rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Programming Language]] vì compiler hiện thực rule của language
- [[Syntax]] vì compiler phải đọc source đúng grammar
- [[Semantics]] vì compiled output phải giữ đúng meaning của chương trình
- [[Static Typing]] vì nhiều compiler chạy type checking trước execution
- [[Runtime]] vì compiled program vẫn có thể cần runtime support

## Liên quan rộng

- Build system
- Type checker
- Optimization
- Toolchain diagnostics

## Source trace

- Crafting Interpreters
- Engineering a Compiler
- Computer Foundations Map Ch09
