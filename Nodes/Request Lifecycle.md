# Request Lifecycle

Aliases: request flow, vòng đ��i request

Type: Backend Engineering

## Context / Ngữ cảnh

Request Lifecycle xuất hiện khi cần hiểu request đi qua network, middleware, handler, database và response như thế nào.

## Boundary / Ranh giới

### Nó là gì

Request Lifecycle là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Request Lifecycle là routing, middleware, auth, validation, transaction, response và logging.

## Project Role / Vai trò trong dự án

Request Lifecycle giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Request Lifecycle decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Request Lifecycle
- Failure note ghi rõ Request Lifecycle ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Request Lifecycle đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Request Lifecycle không?
- Khi Request Lifecycle fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Request Lifecycle làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Request Lifecycle nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Request Lifecycle nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Request Lifecycle trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Software design
- Debugging
- Operations

## Keywords / Từ khóa tìm kiếm

- Request Lifecycle
- request flow
- vòng đ��i request
- request lifecycle debugging
- request lifecycle design

## Source trace

- Web framework docs; HTTP Semantics RFC
