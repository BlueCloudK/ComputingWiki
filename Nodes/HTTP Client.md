# HTTP Client

Aliases: API client, web client, client gọi HTTP

Type: Web Development / API

## Context / Ngữ cảnh

HTTP Client xuất hiện khi frontend/server/mobile cần gửi request HTTP tới backend hoặc third-party API.

## Boundary / Ranh giới

### Nó là gì

HTTP Client là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của HTTP Client là request construction, header, timeout, retry, auth token và response parsing.

## Project Role / Vai trò trong dự án

HTTP Client giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- HTTP Client decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới HTTP Client
- Failure note ghi rõ HTTP Client ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- HTTP Client đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của HTTP Client không?
- Khi HTTP Client fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của HTTP Client làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên HTTP Client nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu HTTP Client nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh HTTP Client trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Frontend architecture
- Browser debugging
- User experience

## Keywords / Từ khóa tìm kiếm

- HTTP Client
- API client
- web client
- client gọi HTTP
- http client debugging
- http client design
- web development
- frontend debugging
- phát triển web

## Source trace

- MDN Fetch API; HTTP Semantics RFC
