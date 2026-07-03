# MongoDB

Aliases: MongoDB, Mongo database, document database

Type: Database / Tool

## Context / Ngữ cảnh

MongoDB là document database dùng BSON/JSON-like document, flexible schema, index và replica set/sharding cho application data.

## Boundary / Ranh giới

### Nó là gì

Nó là database document-oriented, phù hợp khi aggregate document và access pattern quan trọng hơn join quan hệ truyền thống.

### Nó không phải là gì

Nó không có nghĩa là không cần schema design; document shape, index và consistency vẫn phải thiết kế theo query pattern.

## Core Mechanism / Cơ chế lõi

MongoDB lưu document trong collection, dùng index để truy vấn, replica set cho availability và transaction/session cho một số consistency boundary.

## Project Role / Vai trò trong dự án

Node này giúp debug schema drift, missing index, document growth, aggregation pipeline, replica lag và consistency expectation.

## Output / Artifact nên có

- Document model theo access pattern
- Index list cho query chính
- Validation rule hoặc schema convention nếu dữ liệu quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Data nên embed hay reference?
- Query thường dùng có index phù hợp không?
- Document có thể phình lớn theo thời gian không?
- App có cần transaction multi-document không?

## Failure Modes / Cách nó gây lỗi

- Flexible schema thành dữ liệu không đồng nhất khó migrate
- Missing index làm collection scan khi dữ liệu lớn
- Embed quá nhiều làm document growth và update tốn kém

## Khi nào chưa cần hoặc dễ over-engineer

- Không cần MongoDB chỉ vì muốn “schema-less” nếu domain quan hệ rõ
- Dễ over-engineer nếu dùng sharding trước khi có data volume/access pattern thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Document Model]] vì document shape là design decision chính
- [[Database Index]] vì query performance phụ thuộc index

## Liên quan rộng

- NoSQL database
- Backend persistence
- Data modeling

## Keywords / Từ khóa tìm kiếm

- MongoDB
- document database
- BSON
- collection
- replica set
- aggregation pipeline
- schema validation
- NoSQL

## Source trace

- MongoDB official documentation
