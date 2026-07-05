# Prepared Statement

Aliases: Prepared Statement, parameterized statement

Type: Database Internals

## Context / Ngữ cảnh

Prepared Statement xuất hiện khi ứng dụng cần chạy SQL với tham số một cách an toàn, lặp lại và tránh ghép chuỗi query thủ công.

## Boundary / Ranh giới

### Nó là gì

Prepared Statement là SQL statement được chuẩn bị với placeholder tham số, sau đó bind value riêng khi execute.

### Nó không phải là gì

Prepared Statement không phải tự động làm mọi query nhanh hơn. Nó chủ yếu giúp tách cấu trúc SQL khỏi dữ liệu và giảm risk SQL injection.

## Core Mechanism / Cơ chế lõi

Database/driver parse statement với placeholder, app bind parameter theo type, rồi execute. Vì value không được nối trực tiếp vào SQL string, input user không biến thành SQL syntax.

## Project Role / Vai trò trong dự án

Dùng node này khi review data access layer, chống SQL injection, debug query parameter, cache plan hoặc thiết kế repository/service DB access.

## Output / Artifact nên có

- SQL statement có placeholder
- Parameter binding list
- Type mapping note
- Test cho malicious input
- Query plan note nếu performance quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Query có ghép chuỗi user input không?
- Placeholder có bind đủ tham số không?
- Type parameter có khớp column không?
- Dynamic SQL phần identifier có được allowlist không?
- Có test injection case chưa?

## Failure Modes / Cách nó gây lỗi

- Chỉ prepared value nhưng vẫn nối table/column/order by từ input.
- Bind sai type làm query chậm hoặc lỗi.
- Thiếu parameter làm runtime error.
- Plan cache không phù hợp với dữ liệu skew.
- ORM raw query bỏ qua parameter binding.

## Khi nào chưa cần hoặc dễ over-engineer

- Query do ORM/query builder generate an toàn có thể không cần viết prepared statement thủ công.
- Không nên dùng prepared statement để che dynamic SQL thiết kế sai.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[SQL Injection]] vì prepared statement là defense chính chống SQL injection.
- [[Input Validation]] vì validation vẫn cần cho domain rule và identifier allowlist.
- [[Repository]] vì repository thường chứa query parameterized.
- [[Query Plan]] vì prepared query có thể ảnh hưởng plan/caching.

## Liên quan rộng

- Parameter binding
- SQL safety
- Database driver

## Keywords / Từ khóa tìm kiếm

- Prepared Statement
- parameterized statement
- parameter binding
- SQL placeholder
- SQL injection prevention
- prepared statement debugging

## Source trace

- PostgreSQL documentation
- OWASP SQL Injection Prevention Cheat Sheet
