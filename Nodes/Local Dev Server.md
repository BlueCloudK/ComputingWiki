# Local Dev Server

Aliases: Local Dev Server, local dev server

Type: Frameworks and Tools

## Context / Ngữ cảnh

Local Dev Server xuất hiện trong frameworks and tools gom các công cụ ổn định quanh version control, package management, build, test, lint, release và local development.

## Boundary / Ranh giới

### Nó là gì

Local Dev Server là khái niệm giúp đặt tên đúng một cơ chế, artifact hoặc decision trong vùng Frameworks and Tools.

### Nó không phải là gì

Nó không phải tutorial hoặc tên tool để học thuộc; node này dùng để nối concept với project workflow, debug và source trace.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Local Dev Server giải quyết boundary nào, tạo artifact gì, và failure mode nào cần kiểm tra.

## Project Role / Vai trò trong dự án

Local Dev Server giúp chọn đúng abstraction, config, test hoặc debug path khi làm project thật.

## Output / Artifact nên có

- Note hoặc config liên quan tới Local Dev Server
- Test/checklist nếu behavior ảnh hưởng user hoặc release
- Debug signal nếu lỗi thường xuất hiện ở runtime

## Decision Checklist / Câu hỏi kiểm tra

- Local Dev Server nằm ở layer, runtime, build hay operation boundary nào?
- Có source trace và artifact đủ rõ để người khác tiếp tục không?
- Nếu dùng sai, lỗi sẽ lộ ở compile, test, runtime hay production?

## Failure Modes / Cách nó gây lỗi

- Dùng Local Dev Server như keyword chung làm graph nhiễu nhưng không giúp debug
- Thiếu test hoặc metric khiến lỗi chỉ lộ khi integration hoặc production
- Chọn tool/pattern trước khi hiểu constraint thật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Local Dev Server nếu project chưa chạm vấn đề liên quan
- Dễ over-engineer nếu thêm abstraction/tool trước khi có failure mode thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application Engineering
- Deployment and Operations
- Programming Languages

## Keywords / Từ khóa tìm kiếm

- Local Dev Server
- local dev server
- local dev server design
- local dev server debugging
- local dev server production

## Source trace

- Git documentation
- GitHub Actions documentation
- npm documentation
- Maven documentation
- Gradle documentation
