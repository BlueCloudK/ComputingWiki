# Data Representation

Aliases: data encoding, biểu diễn dữ liệu

Type: Computer Foundation

## Context / Ngữ cảnh

Data Representation xuất hiện khi dữ liệu trong code, memory, file hoặc network phải được mã hóa thành bit/byte.

## Boundary / Ranh giới

### Nó là gì

Data Representation là cách map dữ liệu như số, text, boolean, object hoặc record sang dạng máy lưu/truyền được.

### Nó không phải là gì

Nó không phải database model, UI format, hay guarantee dữ liệu đúng về mặt domain.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là encoding/decoding: layout, type, size, endian, charset hoặc schema biến value thành bytes và ngược lại.

## Project Role / Vai trò trong dự án

Node này giúp debug serialization, file format, protocol payload và mismatch giữa systems.

## Output / Artifact nên có

- Encoding/schema note cho dữ liệu qua file, memory, API hoặc network
- Compatibility note khi producer/consumer đọc cùng data
- Decode/round-trip test cho format quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu này là value, text, bytes hay object serialized?
- Encoding/charset/schema có thống nhất giữa hai bên không?
- Có mất thông tin khi convert qua format khác không?

## Failure Modes / Cách nó gây lỗi

- Decode sai charset/endian/schema làm data rác
- Producer đổi representation nhưng consumer không biết
- Round-trip làm mất precision hoặc field optional

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu data chỉ sống trong cùng process/runtime
- Dễ over-engineer nếu tự thiết kế format khi JSON/protobuf/SQL schema đã đủ

## Gồm những gì

- [[Data Type]]
- [[Binary Representation]]

## Nối mạnh

- [[JSON]] vì JSON là một dạng biểu diễn dữ liệu trao đổi
- [[Protocol Buffers]] vì protobuf là biểu diễn schema-based

## Liên quan rộng

- Serialization
- Encoding

## Keywords / Từ khóa tìm kiếm

- Data Representation
- binary representation
- encoding
- bits bytes
- numeric representation
- biểu diễn dữ liệu

## Source trace

- Computer Foundations Map Ch03
