# Server Component

Aliases: Server Component, server component

Type: Frontend Framework

## Context / Ngữ cảnh

Server Component xuất hiện trong frontend frameworks mở rộng component model, state, routing, rendering, build và testing trong web application hiện đại.

## Boundary / Ranh giới

### Nó là gì

Server Component là khái niệm giúp đặt tên đúng một cơ chế, artifact hoặc decision trong vùng Frontend Framework.

### Nó không phải là gì

Nó không phải tutorial hoặc tên tool để học thuộc; node này dùng để nối concept với project workflow, debug và source trace.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Server Component giải quyết boundary nào, tạo artifact gì, và failure mode nào cần kiểm tra.

## Project Role / Vai trò trong dự án

Server Component giúp chọn đúng abstraction, config, test hoặc debug path khi làm project thật.

## Output / Artifact nên có

- Note hoặc config liên quan tới Server Component
- Test/checklist nếu behavior ảnh hưởng user hoặc release
- Debug signal nếu lỗi thường xuất hiện ở runtime

## Decision Checklist / Câu hỏi kiểm tra

- Server Component nằm ở layer, runtime, build hay operation boundary nào?
- Có source trace và artifact đủ rõ để người khác tiếp tục không?
- Nếu dùng sai, lỗi sẽ lộ ở compile, test, runtime hay production?

## Failure Modes / Cách nó gây lỗi

- Dùng Server Component như keyword chung làm graph nhiễu nhưng không giúp debug
- Thiếu test hoặc metric khiến lỗi chỉ lộ khi integration hoặc production
- Chọn tool/pattern trước khi hiểu constraint thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Server Component nếu project chưa chạm vấn đề liên quan
- Dễ over-engineer nếu thêm abstraction/tool trước khi có failure mode thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Web Development
- Programming Languages
- Application Engineering

## Keywords / Từ khóa tìm kiếm

- Server Component
- server component
- server component design
- server component debugging
- server component production

## Source trace

- React documentation
- Vue documentation
- Angular documentation
- MDN Web Docs
