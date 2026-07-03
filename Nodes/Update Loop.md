# Update Loop

Aliases: Update Loop, update loop

Type: Game Development

## Context / Ngữ cảnh

Update Loop xuất hiện trong game development mở rộng game loop, rendering, physics, input, gameplay systems, asset pipeline và engine architecture.

## Boundary / Ranh giới

### Nó là gì

Update Loop là khái niệm giúp đặt tên đúng một cơ chế, artifact hoặc decision trong vùng Game Development.

### Nó không phải là gì

Nó không phải tutorial hoặc tên tool để học thuộc; node này dùng để nối concept với project workflow, debug và source trace.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Update Loop giải quyết boundary nào, tạo artifact gì, và failure mode nào cần kiểm tra.

## Project Role / Vai trò trong dự án

Update Loop giúp chọn đúng abstraction, config, test hoặc debug path khi làm project thật.

## Output / Artifact nên có

- Note hoặc config liên quan tới Update Loop
- Test/checklist nếu behavior ảnh hưởng user hoặc release
- Debug signal nếu lỗi thường xuất hiện ở runtime

## Decision Checklist / Câu hỏi kiểm tra

- Update Loop nằm ở layer, runtime, build hay operation boundary nào?
- Có source trace và artifact đủ rõ để người khác tiếp tục không?
- Nếu dùng sai, lỗi sẽ lộ ở compile, test, runtime hay production?

## Failure Modes / Cách nó gây lỗi

- Dùng Update Loop như keyword chung làm graph nhiễu nhưng không giúp debug
- Thiếu test hoặc metric khiến lỗi chỉ lộ khi integration hoặc production
- Chọn tool/pattern trước khi hiểu constraint thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Update Loop nếu project chưa chạm vấn đề liên quan
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

- Update Loop
- update loop
- update loop design
- update loop debugging
- update loop production

## Source trace

- Game Programming Patterns
- Unity documentation
- Unreal Engine documentation
- Godot documentation
