# ACID

Aliases: atomicity consistency isolation durability, tính chất ACID

Type: Database Systems

## Context / Ngữ cảnh

ACID xuất hiện khi transaction database cần đảm bảo thay đổi dữ liệu đáng tin cậy khi nhiều thao tác xảy ra cùng lúc.

## Boundary / Ranh giới

### Nó là gì

ACID là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của ACID là atomic commit, consistency constraint, isolation boundary và durable log.

## Project Role / Vai trò trong dự án

ACID giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- ACID decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới ACID
- Failure note ghi rõ ACID ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- ACID đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của ACID không?
- Khi ACID fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của ACID làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên ACID nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu ACID nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh ACID trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness

## Keywords / Từ khóa tìm kiếm

- ACID
- atomicity consistency isolation durability
- tính chất ACID
- acid debugging
- acid design
- database design
- debug database
- cơ sở dữ liệu

## Source trace

- Database System Concepts; PostgreSQL docs
