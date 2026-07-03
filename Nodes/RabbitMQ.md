# RabbitMQ

Aliases: RabbitMQ, AMQP broker, message broker

Type: Messaging / Queue

## Context / Ngữ cảnh

RabbitMQ là message broker thường dùng cho task queue, async workflow, routing message và integration giữa service.

## Boundary / Ranh giới

### Nó là gì

Nó là broker nhận message từ producer, route qua exchange/queue và giao cho consumer theo acknowledgement/retry policy.

### Nó không phải là gì

Nó không phải event log để replay dài hạn như Kafka, và không tự làm business operation exactly-once.

## Core Mechanism / Cơ chế lõi

Producer publish message vào exchange, exchange route tới queue, consumer nhận message và ack/nack để broker biết xử lý tiếp.

## Project Role / Vai trò trong dự án

Node này giúp debug queue backlog, retry/dead-letter, consumer crash, duplicate processing và async side effect.

## Output / Artifact nên có

- Exchange/queue routing map
- Retry và dead-letter policy
- Consumer ack/idempotency rule

## Decision Checklist / Câu hỏi kiểm tra

- Message cần routing kiểu direct, topic hay fanout?
- Consumer ack sau khi side effect an toàn chưa?
- Retry có giới hạn và dead-letter queue không?
- Message có idempotency key để xử lý duplicate không?

## Failure Modes / Cách nó gây lỗi

- Consumer ack quá sớm làm mất message khi side effect fail
- Retry vô hạn tạo queue backlog hoặc poison message loop
- Queue durability/config sai làm mất message khi broker restart

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần RabbitMQ nếu task async ít và platform đã có job queue đủ dùng
- Dễ over-engineer nếu tách service bằng message trước khi boundary nghiệp vụ rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Message Broker]] vì RabbitMQ là broker message điển hình
- [[Task Queue]] vì RabbitMQ thường đứng sau background job queue

## Liên quan rộng

- Async processing
- Integration
- Reliability

## Keywords / Từ khóa tìm kiếm

- RabbitMQ
- AMQP
- message broker
- exchange
- queue
- dead letter queue
- consumer ack
- task queue

## Source trace

- RabbitMQ official documentation
