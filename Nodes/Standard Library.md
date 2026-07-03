# Standard Library

Aliases: Standard Library, standard library

Type: Programming Languages Deep

## Context / Ngữ cảnh

Standard Library xuất hiện trong programming languages deep mở rộng semantics, runtime, type system, memory management, concurrency và language implementation concepts.

## Boundary / Ranh giới

### Nó là gì

Standard Library là khái niệm giúp đặt tên đúng một cơ chế, artifact hoặc decision trong vùng Programming Languages Deep.

### Nó không phải là gì

Nó không phải tutorial hoặc tên tool để học thuộc; node này dùng để nối concept với project workflow, debug và source trace.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Standard Library giải quyết boundary nào, tạo artifact gì, và failure mode nào cần kiểm tra.

## Project Role / Vai trò trong dự án

Standard Library giúp chọn đúng abstraction, config, test hoặc debug path khi làm project thật.

## Output / Artifact nên có

- Note hoặc config liên quan tới Standard Library
- Test/checklist nếu behavior ảnh hưởng user hoặc release
- Debug signal nếu lỗi thường xuất hiện ở runtime

## Decision Checklist / Câu hỏi kiểm tra

- Standard Library nằm ở layer, runtime, build hay operation boundary nào?
- Có source trace và artifact đủ rõ để người khác tiếp tục không?
- Nếu dùng sai, lỗi sẽ lộ ở compile, test, runtime hay production?

## Failure Modes / Cách nó gây lỗi

- Dùng Standard Library như keyword chung làm graph nhiễu nhưng không giúp debug
- Thiếu test hoặc metric khiến lỗi chỉ lộ khi integration hoặc production
- Chọn tool/pattern trước khi hiểu constraint thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Standard Library nếu project chưa chạm vấn đề liên quan
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

- Standard Library
- standard library
- standard library design
- standard library debugging
- standard library production

## Source trace

- Types and Programming Languages
- Crafting Interpreters
- Engineering a Compiler
- LLVM documentation
