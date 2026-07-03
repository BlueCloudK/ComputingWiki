# Serializable

Aliases: serializable isolation, cô lập tuần tự

Type: Database Systems

## Context / Ngữ cảnh

Serializable xuất hiện khi transaction cần kết quả tương đương chạy tuần tự để bảo vệ invariant mạnh.

## Boundary / Ranh giới

### Nó là gì

Serializable là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Serializable là serialization conflict, predicate lock/SSI, retry transaction và correctness guarantee.

## Project Role / Vai trò trong dự án

Serializable giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Serializable decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Serializable
- Failure note ghi rõ Serializable ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Serializable đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Serializable không?
- Khi Serializable fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Serializable làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Serializable nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Serializable nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Serializable trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- Serializable
- serializable isolation
- cô lập tuần tự
- serializable debugging
- serializable design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- PostgreSQL Serializable docs; Designing Data-Intensive Applications Ch07
