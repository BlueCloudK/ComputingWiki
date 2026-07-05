# Serverless Function

Aliases: Serverless Function, cloud function

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Serverless Function xuất hiện khi một đoạn logic nhỏ cần chạy theo event/request mà không tự quản lý server dài hạn.

## Boundary / Ranh giới

### Nó là gì

Serverless Function là compute unit được cloud/platform chạy theo trigger như HTTP request, queue message, schedule, storage event hoặc webhook.

### Nó không phải là gì

Serverless Function không có nghĩa là không có server. Server được provider quản lý, nhưng team vẫn chịu trách nhiệm code, timeout, dependency, permission, observability và cost.

## Core Mechanism / Cơ chế lõi

Platform nhận event, khởi tạo runtime nếu cần, chạy handler, trả response/result và ghi log/metric. Function thường có timeout, memory limit, cold start và permission scope riêng.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế webhook, background task nhỏ, scheduled job, lightweight API endpoint hoặc event-driven integration.

## Output / Artifact nên có

- Function handler
- Trigger config
- Runtime/memory/timeout setting
- IAM/secret config
- Log/metric/error handling

## Decision Checklist / Câu hỏi kiểm tra

- Trigger là gì?
- Function có idempotent không?
- Timeout/memory có đủ không?
- Permission có least privilege không?
- Cold start có ảnh hưởng user không?

## Failure Modes / Cách nó gây lỗi

- Timeout làm job chạy dở.
- Cold start làm latency cao.
- Retry event không idempotent gây duplicate side effect.
- Permission quá rộng hoặc thiếu quyền cần thiết.
- Log thiếu correlation id nên debug khó.

## Khi nào chưa cần hoặc dễ over-engineer

- Service stateful hoặc long-running có thể không hợp serverless function.
- Không nên chia quá nhiều function nhỏ nếu observability và deployment trở nên rối.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Timeout]] vì function luôn có giới hạn thời gian chạy.
- [[Least Privilege]] vì function IAM nên scope nhỏ.
- [[Logging]] vì debug serverless phụ thuộc log tốt.
- [[API Endpoint]] vì HTTP function có thể là endpoint.

## Liên quan rộng

- Event-driven architecture
- Cloud runtime
- Webhook handler

## Keywords / Từ khóa tìm kiếm

- Serverless Function
- cloud function
- function as a service
- cold start
- event trigger
- serverless timeout
- serverless function debugging

## Source trace

- AWS Lambda documentation
- Google Cloud Functions documentation
