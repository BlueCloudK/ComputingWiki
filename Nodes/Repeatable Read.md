# Repeatable Read

Aliases: repeatable read isolation, đọc lặp lại

Type: Database Systems

## Context / Ngữ cảnh

Repeatable Read xuất hiện khi transaction cần view ổn định hơn để tránh non-repeatable read.

## Boundary / Ranh giới

### Nó là gì

Repeatable Read là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Repeatable Read là transaction snapshot, row visibility, phantom behavior tùy DB implementation.

## Project Role / Vai trò trong dự án

Repeatable Read giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Repeatable Read decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Repeatable Read
- Failure note ghi rõ Repeatable Read ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Repeatable Read đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Repeatable Read không?
- Khi Repeatable Read fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Repeatable Read làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Repeatable Read nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Repeatable Read nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Repeatable Read trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Repeatable Read
- repeatable read isolation
- đọc lặp lại
- repeatable read debugging
- repeatable read design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL transaction isolation docs; MySQL docs
