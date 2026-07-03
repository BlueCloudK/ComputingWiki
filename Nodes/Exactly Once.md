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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Idempotency]] vì exactly-once thường cần idempotent side effects
- [[Transaction]] vì atomic commit giúp tránh partial effect

## Liên quan rộng

- Stream processing guarantees

## Source trace

- DDIA Ch11
