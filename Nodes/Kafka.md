# Kafka

Aliases: Apache Kafka, Kafka, event streaming platform

Type: Messaging / Data Platform

## Context / Ngữ cảnh

Kafka là distributed event streaming platform dùng topic, partition và consumer group để xử lý event/log stream ở quy mô lớn.

## Boundary / Ranh giới

### Nó là gì

Nó là commit log phân tán cho message/event stream, hỗ trợ replay, ordering trong partition và consumer scaling qua group.

### Nó không phải là gì

Nó không tự bảo đảm exactly-once business outcome nếu producer/consumer/database boundary không idempotent.

## Core Mechanism / Cơ chế lõi

Producer ghi record vào topic partition, broker lưu log theo offset, consumer group đọc offset và commit progress.

## Project Role / Vai trò trong dự án

Node này giúp debug event-driven architecture, consumer lag, partition key, replay, schema evolution và duplicate processing.

## Output / Artifact nên có

- Topic/partition design
- Consumer group ownership
- Schema và retention policy cho event

## Decision Checklist / Câu hỏi kiểm tra

- Partition key có giữ ordering cần thiết không?
- Consumer có idempotent khi xử lý lại message không?
- Retention có đủ cho replay/debug không?
- Schema evolution có backward/forward compatibility không?

## Failure Modes / Cách nó gây lỗi

- Partition key sai làm hot partition hoặc mất ordering cần thiết
- Consumer commit offset trước khi side effect an toàn
- Lag tăng nhưng alert không phân biệt backlog bình thường và sự cố

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Kafka cho vài job async nhỏ có queue đơn giản là đủ
- Dễ over-engineer nếu dùng event streaming trước khi domain event và consumer rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Event Driven Architecture]] vì Kafka thường là backbone event stream
- [[At Least Once]] vì Kafka consumer thường phải xử lý retry/duplicate

## Liên quan rộng

- Stream processing
- Data pipeline
- Messaging

## Keywords / Từ khóa tìm kiếm

- Kafka
- Apache Kafka
- event streaming
- topic
- partition
- consumer group
- consumer lag
- offset

## Source trace

- Apache Kafka official documentation
