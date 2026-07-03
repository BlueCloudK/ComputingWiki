# Write Ahead Log

Aliases: WAL, transaction log, log ghi trước

Type: Database Systems

## Context / Ngữ cảnh

Write Ahead Log xuất hiện khi database cần phục hồi sau crash và hỗ trợ replication đáng tin cậy.

## Boundary / Ranh giới

### Nó là gì

Write Ahead Log là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Write Ahead Log là log record, fsync, checkpoint, crash recovery và replication stream.

## Project Role / Vai trò trong dự án

Write Ahead Log giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Write Ahead Log decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Write Ahead Log
- Failure note ghi rõ Write Ahead Log ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Write Ahead Log đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Write Ahead Log không?
- Khi Write Ahead Log fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Write Ahead Log làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Write Ahead Log nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Write Ahead Log nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Write Ahead Log trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Write Ahead Log
- WAL
- transaction log
- log ghi trước
- write ahead log debugging
- write ahead log design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL WAL docs; Database System Concepts
