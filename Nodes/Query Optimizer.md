# Query Optimizer

Aliases: SQL optimizer, bộ tối ưu truy vấn

Type: Database Systems

## Context / Ngữ cảnh

Query Optimizer xuất hiện khi database cần chọn execution plan tốt cho query dựa trên statistics và index.

## Boundary / Ranh giới

### Nó là gì

Query Optimizer là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Query Optimizer là statistics, cardinality estimate, join order, access path và cost model.

## Project Role / Vai trò trong dự án

Query Optimizer giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Query Optimizer decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Query Optimizer
- Failure note ghi rõ Query Optimizer ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Query Optimizer đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Query Optimizer không?
- Khi Query Optimizer fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Query Optimizer làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Query Optimizer nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Query Optimizer nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Query Optimizer trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Query Optimizer
- SQL optimizer
- bộ tối ưu truy vấn
- query optimizer debugging
- query optimizer design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL planner docs; Database System Concepts
