# ORM

Aliases: Object Relational Mapper, object-relational mapping, ánh xạ ORM

Type: Backend Engineering / Database

## Context / Ngữ cảnh

ORM xuất hiện khi code object-oriented cần đọc/ghi relational database mà không viết SQL thủ công ở mọi nơi.

## Boundary / Ranh giới

### Nó là gì

ORM là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của ORM là entity mapping, query builder, lazy/eager load, transaction và change tracking.

## Project Role / Vai trò trong dự án

ORM giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- ORM decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới ORM
- Failure note ghi rõ ORM ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- ORM đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của ORM không?
- Khi ORM fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của ORM làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên ORM nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu ORM nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh ORM trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- ORM
- Object Relational Mapper
- object-relational mapping
- ánh xạ ORM
- orm debugging
- orm design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- Hibernate docs; SQLAlchemy docs; EF Core docs
