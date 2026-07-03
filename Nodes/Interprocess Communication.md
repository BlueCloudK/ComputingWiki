# Interprocess Communication

Aliases: IPC, giao tiếp liên tiến trình

Type: Protocol / Data Format

## Bản chất

Interprocess Communication là quy ước để hệ thống encode, parse, truyền hoặc hiểu dữ liệu/giao tiếp. Vấn đề chính là compatibility: producer và consumer phải thống nhất schema, version, error và behavior khi dữ liệu lệch. Nó nối với các phần liên quan như [[Message Passing]], [[Process]] và nhóm quyết định quanh interprocess communication.

## Dùng trong dự án để làm gì

Interprocess Communication ảnh hưởng tới API payload, message, config, log, network call hoặc storage format. Trong dự án, nó giúp tránh lỗi serialize/parse, client-server mismatch và breaking change giữa service.

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

- [[Message Passing]]

## Liên quan

- [[Process]]

## Source trace

- Operating Systems Map / Ch02.3
