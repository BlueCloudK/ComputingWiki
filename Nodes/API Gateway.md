# API Gateway

Aliases: gateway API, edge gateway, cổng API

Type: API / Infrastructure

## Context / Ngữ cảnh

API Gateway xuất hiện khi API traffic cần entrypoint tập trung cho routing, auth, rate limit hoặc protocol translation.

## Boundary / Ranh giới

### Nó là gì

API Gateway là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của API Gateway là route matching, policy enforcement, upstream selection, timeout và observability.

## Project Role / Vai trò trong dự án

API Gateway giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- API Gateway decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới API Gateway
- Failure note ghi rõ API Gateway ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- API Gateway đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của API Gateway không?
- Khi API Gateway fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của API Gateway làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên API Gateway nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu API Gateway nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh API Gateway trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Platform engineering
- Deployment operations
- Production reliability

## Keywords / Từ khóa tìm kiếm

- API Gateway
- gateway API
- edge gateway
- cổng API
- api gateway debugging
- api gateway design
- deployment config
- vận hành hạ tầng

## Source trace

- AWS API Gateway docs; Envoy docs
