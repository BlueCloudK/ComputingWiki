# Interpreter

Aliases: interpreter, trình thông dịch

Type: Computer Foundation

## Context / Ngữ cảnh

Interpreter xuất hiện khi chương trình được thực thi bằng cách đọc representation của code và chạy behavior trực tiếp qua một evaluator/runtime thay vì chỉ sinh artifact trước.

## Boundary / Ranh giới

### Nó là gì

Interpreter là chương trình thực thi source hoặc intermediate representation bằng cách evaluate construct theo semantics của language.

### Nó không phải là gì

Nó không phải là compiler, không phải REPL đơn thuần, và không có nghĩa là language không có bước parse/check/cache nào trước khi chạy.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là evaluation loop: nhận construct, resolve environment/state, thực hiện operation, trả value hoặc error. Interpreter thường gắn chặt với runtime, scope và object/value representation.

## Project Role / Vai trò trong dự án

Interpreter ảnh hưởng startup behavior, runtime error timing, debugging, scripting flexibility và performance profile. Hiểu interpreter giúp phân biệt lỗi parse/check với lỗi chỉ xuất hiện khi execution đi tới path đó.

## Output / Artifact nên có

- Runtime/interpreter version cần cho project
- Note về evaluation model hoặc runtime behavior quan trọng
- Diagnostic/log khi runtime path gây lỗi

## Decision Checklist / Câu hỏi kiểm tra

- Code được interpret trực tiếp hay có bytecode/JIT/cache?
- Lỗi này xuất hiện khi parse, load module hay evaluate path?
- Environment/scope nào được interpreter dùng khi resolve name?
- Runtime version có ảnh hưởng behavior không?
- Performance issue đến từ interpretation, IO hay algorithm?

## Failure Modes / Cách nó gây lỗi

- Nghĩ dynamic/interpreted code không có phase check nào
- Runtime error chỉ lộ ở path hiếm vì không có static check đủ mạnh
- Environment/module resolution khác dev-production
- Đổ lỗi cho interpreter performance khi bottleneck thật là IO hoặc algorithm

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần interpreter internals nếu chỉ chạy script nhỏ và lỗi rõ
- Dễ over-engineer nếu phân tích VM/evaluator sâu trước khi có bug hoặc design need

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Programming Language]] vì interpreter thực thi semantics của language
- [[Runtime]] vì interpreter thường là trung tâm của runtime execution
- [[Dynamic Typing]] vì nhiều interpreted languages kiểm tra type trong runtime
- [[Semantics]] vì interpreter encode nghĩa của construct khi evaluate

## Liên quan rộng

- REPL
- Virtual machine
- Scripting
- Runtime diagnostics

## Keywords / Từ khóa tìm kiếm

- Interpreter
- program interpreter
- runtime execution
- eval loop
- bytecode interpreter
- scripting runtime
- trình thông dịch

## Source trace

- Crafting Interpreters
- Computer Foundations Map Ch09
