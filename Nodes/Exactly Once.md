# Exactly Once

Aliases: exactly-once processing, xử lý đúng một lần

Type: Data / Database

## Context / Ngữ cảnh

Exactly Once xuất hiện khi pipeline/message system muốn tránh duplicate và loss trong xử lý event.

## Boundary / Ranh giới

### Nó là gì

Exactly Once là guarantee rằng effect quan trọng được quan sát như xảy ra đúng một lần.

### Nó không phải là gì

Nó không có nghĩa network không retry và thường là end-to-end effect chứ không phải delivery vật lý.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là kết hợp idempotency, transaction, offset/commit và deduplication để tạo result đúng.

## Project Role / Vai trò trong dự án

Node này giúp thiết kế payment, event processing và stream job không duplicate side effect.

## Output / Artifact nên có

- Exactly-once boundary statement
- Dedup/idempotency key storage
- Atomic commit hoặc offset-handling note

## Decision Checklist / Câu hỏi kiểm tra

- Exactly once áp dụng cho delivery, processing hay side effect?
- Dedup record có commit cùng side effect không?
- Retry sau crash có tạo lại effect không?

## Failure Modes / Cách nó gây lỗi

- Tin broker exactly-once nhưng sink vẫn duplicate
- Commit offset trước side effect làm mất event
- Dedup TTL quá ngắn tạo effect lần hai

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu duplicate không gây hại
- Dễ over-engineer nếu at-least-once + idempotency đủ cho business

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Idempotency]] vì exactly-once thường cần idempotent side effects
- [[Transaction]] vì atomic commit giúp tránh partial effect

## Liên quan rộng

- Stream processing guarantees

## Keywords / Từ khóa tìm kiếm

- Exactly Once
- exactly once delivery
- duplicate processing
- message semantics
- transactional messaging
- xử lý đúng một lần

## Source trace

- DDIA Ch11
