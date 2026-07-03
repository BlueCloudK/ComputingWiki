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

- Type list cho model/API quan trọng
- Conversion rule giữa primitive, object và serialized form
- Validation note cho dữ liệu ngoài đi vào type nội bộ

## Decision Checklist / Câu hỏi kiểm tra

- Type này bảo vệ meaning domain nào?
- Có đang dùng string/number quá rộng thay vì domain type không?
- Runtime input có được validate trước khi tin vào type không?

## Failure Modes / Cách nó gây lỗi

- Primitive obsession làm mất invariant
- Implicit conversion đổi nghĩa dữ liệu
- Type trong code không khớp shape từ API/database

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách type riêng cho field nhỏ ít rủi ro
- Dễ over-engineer nếu mọi field đều thành abstraction riêng không bảo vệ invariant

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Type System]] vì type system kiểm tra và tổ chức data type
- [[Data Representation]] vì type quyết định cách data được encode/store

## Liên quan rộng

- Primitive type
- Composite type

## Keywords / Từ khóa tìm kiếm

- Data Type
- type of data
- kiểu dữ liệu
- data
- type
- Computer Foundation
- dữ liệu
- hệ thống dữ liệu

## Source trace

- Computer Foundations Map Ch03
- Types and Programming Languages
