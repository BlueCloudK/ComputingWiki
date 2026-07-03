# SWR

Aliases: SWR, swr

Type: Frontend Framework

## Context / Ngữ cảnh

SWR xuất hiện trong frontend frameworks mở rộng component model, state, routing, rendering, build và testing trong web application hiện đại.

## Boundary / Ranh giới

### Nó là gì

SWR là khái niệm giúp đặt tên đúng một cơ chế, artifact hoặc decision trong vùng Frontend Framework.

### Nó không phải là gì

Nó không phải tutorial hoặc tên tool để học thuộc; node này dùng để nối concept với project workflow, debug và source trace.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu SWR giải quyết boundary nào, tạo artifact gì, và failure mode nào cần kiểm tra.

## Project Role / Vai trò trong dự án

SWR giúp chọn đúng abstraction, config, test hoặc debug path khi làm project thật.

## Output / Artifact nên có

- Note hoặc config liên quan tới SWR
- Test/checklist nếu behavior ảnh hưởng user hoặc release
- Debug signal nếu lỗi thường xuất hiện ở runtime

## Decision Checklist / Câu hỏi kiểm tra

- SWR nằm ở layer, runtime, build hay operation boundary nào?
- Có source trace và artifact đủ rõ để người khác tiếp tục không?
- Nếu dùng sai, lỗi sẽ lộ ở compile, test, runtime hay production?

## Failure Modes / Cách nó gây lỗi

- Dùng SWR như keyword chung làm graph nhiễu nhưng không giúp debug
- Thiếu test hoặc metric khiến lỗi chỉ lộ khi integration hoặc production
- Chọn tool/pattern trước khi hiểu constraint thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu SWR nếu project chưa chạm vấn đề liên quan
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

- SWR
- swr
- swr design
- swr debugging
- swr production

## Source trace

- React documentation
- Vue documentation
- Angular documentation
- MDN Web Docs
