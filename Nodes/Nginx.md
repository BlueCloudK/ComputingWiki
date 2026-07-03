# Nginx

Aliases: nginx web server, nginx reverse proxy

Type: Infrastructure / Web

## Context / Ngữ cảnh

Nginx xuất hiện khi cần web server hoặc reverse proxy cho static file, TLS termination, routing và load balancing.

## Boundary / Ranh giới

### Nó là gì

Nginx là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Nginx là server block, location, upstream, proxy headers và buffering.

## Project Role / Vai trò trong dự án

Nginx giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Nginx decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Nginx
- Failure note ghi rõ Nginx ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Nginx đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Nginx không?
- Khi Nginx fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Nginx làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Nginx nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Nginx nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Nginx trước khi có nhu cầu vận hành hoặc học tập rõ

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

- Nginx
- nginx web server
- nginx reverse proxy
- nginx debugging
- nginx design
- deployment config
- vận hành hạ tầng
- web development
- frontend debugging
- phát triển web

## Source trace

- Nginx docs
