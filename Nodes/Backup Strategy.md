# Backup Strategy

Aliases: database backup strategy, chiến lược backup

Type: Database Systems / Operations

## Context / Ngữ cảnh

Backup Strategy xuất hiện khi dữ liệu cần phục hồi sau lỗi vận hành, corruption hoặc disaster.

## Boundary / Ranh giới

### Nó là gì

Backup Strategy là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Backup Strategy là full/incremental backup, PITR, retention, restore test và RPO/RTO.

## Project Role / Vai trò trong dự án

Backup Strategy giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Backup Strategy decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Backup Strategy
- Failure note ghi rõ Backup Strategy ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Backup Strategy đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Backup Strategy không?
- Khi Backup Strategy fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Backup Strategy làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Backup Strategy nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Backup Strategy nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Backup Strategy trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Backup Strategy
- database backup strategy
- chiến lược backup
- backup strategy debugging
- backup strategy design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL backup docs; Google SRE Book
