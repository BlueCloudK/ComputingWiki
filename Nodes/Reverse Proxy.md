# Reverse Proxy

Aliases: proxy ngược, HTTP reverse proxy

Type: Infrastructure / Web

## Context / Ngữ cảnh

Reverse Proxy xuất hiện khi server đứng trước app/backend để nhận client traffic và chuyển tiếp tới upstream phù hợp.

## Boundary / Ranh giới

### Nó là gì

Reverse Proxy là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Reverse Proxy là upstream routing, TLS termination, header forwarding, buffering và health check.

## Project Role / Vai trò trong dự án

Reverse Proxy giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Reverse Proxy decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Reverse Proxy
- Failure note ghi rõ Reverse Proxy ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Reverse Proxy đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Reverse Proxy không?
- Khi Reverse Proxy fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Reverse Proxy làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Reverse Proxy nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Reverse Proxy nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Reverse Proxy trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability
- Frontend architecture
- Browser debugging
- User experience

## Keywords / Từ khóa tìm kiếm

- Reverse Proxy
- proxy ngược
- HTTP reverse proxy
- reverse proxy debugging
- reverse proxy design
- deployment config
- vận hành hạ tầng
- web development
- frontend debugging
- phát triển web

## Source trace

- Nginx docs; Envoy docs
