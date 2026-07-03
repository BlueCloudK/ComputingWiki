# Connection Pooling

Aliases: database connection pool, pool kết nối

Type: Backend / Database

## Context / Ngữ cảnh

Connection Pooling xuất hiện khi app cần tái sử dụng connection và kiểm soát concurrency tới database.

## Boundary / Ranh giới

### Nó là gì

Connection Pooling là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Connection Pooling là pool size, checkout timeout, idle connection, max lifetime và leak detection.

## Project Role / Vai trò trong dự án

Connection Pooling giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Connection Pooling decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Connection Pooling
- Failure note ghi rõ Connection Pooling ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Connection Pooling đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Connection Pooling không?
- Khi Connection Pooling fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Connection Pooling làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Connection Pooling nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Connection Pooling nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Connection Pooling trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Connection Pooling
- database connection pool
- pool kết nối
- connection pooling debugging
- connection pooling design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- HikariCP docs; PostgreSQL connection docs
