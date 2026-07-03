# Data Formats

Aliases: serialization formats, định dạng dữ liệu

Type: Protocol / Data Format

## Bản chất

Data Formats là quy ước để hệ thống encode, parse, truyền hoặc hiểu dữ liệu/giao tiếp. Vấn đề chính là compatibility: producer và consumer phải thống nhất schema, version, error và behavior khi dữ liệu lệch. Nó nối với các phần liên quan như [[Encoding and Evolution]], [[JSON]], [[XML]] và nhóm quyết định quanh data formats.

## Dùng trong dự án để làm gì

Data Formats là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

## Khi nào cần quan tâm

- Thiết kế payload, message, config, log hoặc protocol call
- Consumer cũ cần đọc dữ liệu producer mới
- Parse/serialize lỗi hoặc dữ liệu mất kiểu
- Cần versioning/schema để nhiều service cùng hiểu

## Output / artifact nên có

- Schema/contract hoặc format decision ghi rõ field, type và version
- Parser/serializer validation rule và error handling
- Compatibility test cho consumer/producer quan trọng

## Checklist kiểm tra

- Producer và consumer có hiểu cùng schema/type không?
- Versioning/backward compatibility được xử lý thế nào?
- Parse error, missing field và extra field trả lỗi ra sao?
- Date/time/number/binary encoding có rủi ro mất dữ liệu không?
- Payload size hoặc protocol behavior có ảnh hưởng performance không?

## Lỗi / rủi ro thường gặp

- Client/server hiểu khác type hoặc optional field
- Breaking schema làm consumer cũ lỗi
- Date/time/number precision bị serialize sai
- Payload lớn hoặc parsing đắt làm API/log chậm

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần schema/versioning phức tạp khi dữ liệu nội bộ nhỏ và consumer ít
- Dễ over-engineer nếu chọn format/protocol nặng hơn nhu cầu tích hợp thật

## Gồm những gì

- [[Encoding and Evolution]]
- [[JSON]]
- [[XML]]
- [[Protocol Buffers]]
- [[Avro]]
- [[Data Transfer Object]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Data Intensive Applications Map
- Fowler Pattern Map
