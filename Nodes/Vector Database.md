# Vector Database

Aliases: vector DB, cơ sở dữ liệu vector

Type: AI / ML Engineering / Data

## Context / Ngữ cảnh

Vector Database xuất hiện khi embedding cần được lưu và tìm kiếm theo similarity với latency chấp nhận được.

## Boundary / Ranh giới

### Nó là gì

Vector Database là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Vector Database là ANN index, metadata filter, recall/latency trade-off và vector update.

## Project Role / Vai trò trong dự án

Vector Database giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Vector Database decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Vector Database
- Failure note ghi rõ Vector Database ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Vector Database đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Vector Database không?
- Khi Vector Database fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Vector Database làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Vector Database nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Vector Database nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Vector Database trước khi có nhu cầu vận hành hoặc học tập rõ

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

- Vector Database
- vector DB
- cơ sở dữ liệu vector
- vector database debugging
- vector database design
- database design
- debug database
- cơ sở dữ liệu
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- Pinecone docs; Milvus docs; pgvector docs
