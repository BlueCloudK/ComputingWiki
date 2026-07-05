# Make

Aliases: Make, Makefile

Type: Frameworks and Tools

## Context / Ngữ cảnh

Make xuất hiện khi project cần gom các command lặp lại như build, test, lint, clean, run hoặc deploy vào một interface đơn giản.

## Boundary / Ranh giới

### Nó là gì

Make là build automation tool dùng `Makefile` để định nghĩa target, dependency và command.

### Nó không phải là gì

Make không phải package manager và không thay thế build system chuyên sâu nếu project cần dependency graph phức tạp.

## Core Mechanism / Cơ chế lõi

Make đọc target trong `Makefile`, so sánh dependency/file timestamp nếu có, rồi chạy command tương ứng. Trong nhiều project hiện đại, Makefile còn được dùng như command launcher thống nhất.

## Project Role / Vai trò trong dự án

Dùng node này khi chuẩn hóa lệnh local/CI như `make test`, `make build`, `make run` hoặc `make clean`.

## Output / Artifact nên có

- Makefile
- Target list
- Command convention
- CI mapping nếu dùng trong pipeline

## Decision Checklist / Câu hỏi kiểm tra

- Target này chạy command gì?
- Command có idempotent không?
- Local và CI có dùng cùng target không?
- Dependency hoặc env cần thiết có rõ không?

## Failure Modes / Cách nó gây lỗi

- Target tên rõ nhưng command bên trong làm quá nhiều việc.
- Local và CI gọi command khác nhau.
- Makefile phụ thuộc shell/env không document.
- Timestamp/dependency rule sai làm build không chạy lại.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ có vài command package script là đủ.
- Không nên biến Makefile thành deploy framework phức tạp nếu tool chuyên dụng phù hợp hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CLI Tool]] vì Make thường gom các command CLI thành target.
- [[CI]] vì CI có thể gọi target Make để reuse command local.
- [[Build Cache]] vì build target có thể tương tác với cache/output.

## Liên quan rộng

- Build automation
- Developer workflow
- Command runner

## Keywords / Từ khóa tìm kiếm

- Make
- Makefile
- make target
- build automation
- make test
- make build
- Make debugging

## Source trace

- GNU Make documentation
