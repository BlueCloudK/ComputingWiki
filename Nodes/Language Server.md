# Language Server

Aliases: Language Server, language server

Type: Programming Languages Deep

## Context / Ngữ cảnh

Language Server xuất hiện trong programming languages deep mở rộng semantics, runtime, type system, memory management, concurrency và language implementation concepts.

## Boundary / Ranh giới

### Nó là gì

Language Server là khái niệm giúp đặt tên đúng một cơ chế, artifact hoặc decision trong vùng Programming Languages Deep.

### Nó không phải là gì

Nó không phải tutorial hoặc tên tool để học thuộc; node này dùng để nối concept với project workflow, debug và source trace.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Language Server giải quyết boundary nào, tạo artifact gì, và failure mode nào cần kiểm tra.

## Project Role / Vai trò trong dự án

Language Server giúp chọn đúng abstraction, config, test hoặc debug path khi làm project thật.

## Output / Artifact nên có

- Note hoặc config liên quan tới Language Server
- Test/checklist nếu behavior ảnh hưởng user hoặc release
- Debug signal nếu lỗi thường xuất hiện ở runtime

## Decision Checklist / Câu hỏi kiểm tra

- Language Server nằm ở layer, runtime, build hay operation boundary nào?
- Có source trace và artifact đủ rõ để người khác tiếp tục không?
- Nếu dùng sai, lỗi sẽ lộ ở compile, test, runtime hay production?

## Failure Modes / Cách nó gây lỗi

- Dùng Language Server như keyword chung làm graph nhiễu nhưng không giúp debug
- Thiếu test hoặc metric khiến lỗi chỉ lộ khi integration hoặc production
- Chọn tool/pattern trước khi hiểu constraint thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Language Server nếu project chưa chạm vấn đề liên quan
- Dễ over-engineer nếu thêm abstraction/tool trước khi có failure mode thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Programming Languages
- Compiler and Interpreter
- Operating System

## Keywords / Từ khóa tìm kiếm

- Language Server
- language server
- language server design
- language server debugging
- language server production

## Source trace

- Types and Programming Languages
- Crafting Interpreters
- Engineering a Compiler
- LLVM documentation
