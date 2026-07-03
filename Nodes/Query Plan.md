# Query Plan

Aliases: execution plan, kế hoạch truy vấn

Type: Database Systems

## Context / Ngữ cảnh

Query Plan xuất hiện khi cần hiểu database sẽ đọc, join, filter hoặc sort dữ liệu như thế nào.

## Boundary / Ranh giới

### Nó là gì

Query Plan là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Query Plan là scan type, join algorithm, estimated cost, actual timing và row count.

## Project Role / Vai trò trong dự án

Query Plan giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Query Plan decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Query Plan
- Failure note ghi rõ Query Plan ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Query Plan đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Query Plan không?
- Khi Query Plan fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Query Plan làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Query Plan nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Query Plan nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Query Plan trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Query Plan
- execution plan
- kế hoạch truy vấn
- query plan debugging
- query plan design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL EXPLAIN docs
