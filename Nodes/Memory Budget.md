# Memory Budget

Aliases: Memory Budget, memory budget

Type: Game Development

## Context / Ngữ cảnh

Memory Budget xuất hiện trong game development mở rộng game loop, rendering, physics, input, gameplay systems, asset pipeline và engine architecture.

## Boundary / Ranh giới

### Nó là gì

Memory Budget là khái niệm giúp đặt tên đúng một cơ chế, artifact hoặc decision trong vùng Game Development.

### Nó không phải là gì

Nó không phải tutorial hoặc tên tool để học thuộc; node này dùng để nối concept với project workflow, debug và source trace.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Memory Budget giải quyết boundary nào, tạo artifact gì, và failure mode nào cần kiểm tra.

## Project Role / Vai trò trong dự án

Memory Budget giúp chọn đúng abstraction, config, test hoặc debug path khi làm project thật.

## Output / Artifact nên có

- Note hoặc config liên quan tới Memory Budget
- Test/checklist nếu behavior ảnh hưởng user hoặc release
- Debug signal nếu lỗi thường xuất hiện ở runtime

## Decision Checklist / Câu hỏi kiểm tra

- Memory Budget nằm ở layer, runtime, build hay operation boundary nào?
- Có source trace và artifact đủ rõ để người khác tiếp tục không?
- Nếu dùng sai, lỗi sẽ lộ ở compile, test, runtime hay production?

## Failure Modes / Cách nó gây lỗi

- Dùng Memory Budget như keyword chung làm graph nhiễu nhưng không giúp debug
- Thiếu test hoặc metric khiến lỗi chỉ lộ khi integration hoặc production
- Chọn tool/pattern trước khi hiểu constraint thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Memory Budget nếu project chưa chạm vấn đề liên quan
- Dễ over-engineer nếu thêm abstraction/tool trước khi có failure mode thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Programming Languages
- Performance
- Software Architecture

## Keywords / Từ khóa tìm kiếm

- Memory Budget
- memory budget
- memory budget design
- memory budget debugging
- memory budget production

## Source trace

- Game Programming Patterns
- Unity documentation
- Unreal Engine documentation
- Godot documentation
