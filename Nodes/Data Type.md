# Data Type

Aliases: type of data, kiểu dữ liệu

Type: Computer Foundation

## Context / Ngữ cảnh

Data Type xuất hiện khi cần biết một value thuộc loại gì và operation nào hợp lệ trên value đó.

## Boundary / Ranh giới

### Nó là gì

Data Type là phân loại value như number, string, boolean, record, array hoặc custom domain type.

### Nó không phải là gì

Nó không phải Type System toàn bộ, database schema, hay validation dữ liệu ngoài.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gắn meaning và allowed operations cho value để code/tooling xử lý đúng.

## Project Role / Vai trò trong dự án

Node này giúp đọc API payload, domain model và tránh nhầm shape dữ liệu khi refactor.

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

- [[Type System]] vì type system kiểm tra và tổ chức data type
- [[Data Representation]] vì type quyết định cách data được encode/store

## Liên quan rộng

- Primitive type
- Composite type

## Source trace

- Computer Foundations Map Ch03
- Types and Programming Languages
