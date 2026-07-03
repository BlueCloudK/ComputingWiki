# N Plus One Query

Aliases: N+1 query, truy vấn N cộng 1

Type: Failure Pattern / Database

## Context / Ngữ cảnh

N Plus One Query xuất hiện khi code gọi thêm một query cho từng record thay vì fetch theo batch hoặc join.

## Boundary / Ranh giới

### Nó là gì

N Plus One Query là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của N Plus One Query là lazy loading, relation traversal, query count, eager load và batching.

## Project Role / Vai trò trong dự án

N Plus One Query giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- N Plus One Query decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới N Plus One Query
- Failure note ghi rõ N Plus One Query ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- N Plus One Query đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của N Plus One Query không?
- Khi N Plus One Query fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của N Plus One Query làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên N Plus One Query nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu N Plus One Query nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh N Plus One Query trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Database reliability
- Backend performance
- Data correctness
- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- N Plus One Query
- N+1 query
- truy vấn N cộng 1
- n plus one query debugging
- n plus one query design
- database design
- debug database
- cơ sở dữ liệu
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Hibernate docs; Rails ActiveRecord docs
