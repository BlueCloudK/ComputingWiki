# Database Lock

Aliases: DB lock, khóa cơ sở dữ liệu

Type: Database Systems

## Context / Ngữ cảnh

Database Lock xuất hiện khi database cần bảo vệ dữ liệu/schema/resource khi nhiều transaction cạnh tranh.

## Boundary / Ranh giới

### Nó là gì

Database Lock là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Database Lock là row lock, table lock, lock mode, wait queue và deadlock detection.

## Project Role / Vai trò trong dự án

Database Lock giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Database Lock decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Database Lock
- Failure note ghi rõ Database Lock ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Database Lock đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Database Lock không?
- Khi Database Lock fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Database Lock làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Database Lock nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Database Lock nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Database Lock trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Database Lock
- DB lock
- khóa cơ sở dữ liệu
- database lock debugging
- database lock design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL explicit locking docs
