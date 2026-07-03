# HTTP

Aliases: Hypertext Transfer Protocol, giao thức HTTP

Type: Protocol / Data Format

## Context / Ngữ cảnh

HTTP xuất hiện khi hệ thống cần encode, parse, truyền hoặc hiểu dữ liệu/giao tiếp giữa producer và consumer.

## Boundary / Ranh giới

### Nó là gì

HTTP là quy ước compatibility: field/type/version/error behavior phải được hai bên hiểu giống nhau.

### Nó không phải là gì

Nó không chỉ là syntax hoặc format file; nếu thiếu schema/versioning/error handling thì integration vẫn dễ vỡ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là serialization/parsing + schema/contract + compatibility. Producer tạo dữ liệu, consumer parse và xử lý; lỗi xuất hiện khi hai bên hiểu khác nhau.

## Project Role / Vai trò trong dự án

HTTP ảnh hưởng tới API payload, message, config, log, network call hoặc storage format.

## Output / Artifact nên có

- Schema/contract hoặc format decision ghi rõ field, type và version
- Parser/serializer validation rule và error handling
- Compatibility test cho consumer/producer quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Producer và consumer có hiểu cùng schema/type không?
- Versioning/backward compatibility được xử lý thế nào?
- Parse error, missing field và extra field trả lỗi ra sao?
- Date/time/number/binary encoding có rủi ro mất dữ liệu không?
- Payload size hoặc protocol behavior có ảnh hưởng performance không?

## Failure Modes / Cách nó gây lỗi

- Client/server hiểu khác type hoặc optional field
- Breaking schema làm consumer cũ lỗi
- Date/time/number precision bị serialize sai
- Payload lớn hoặc parsing đắt làm API/log chậm

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần schema/versioning phức tạp khi dữ liệu nội bộ nhỏ và consumer ít
- Dễ over-engineer nếu chọn format/protocol nặng hơn nhu cầu tích hợp thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[REST]] vì node này thường được kiểm tra cùng khi ra quyết định

## Liên quan rộng

- Interoperability
- Network communication
- Data exchange
- Backward compatibility

## Source trace

- Computer Networks Map / Ch02.2
