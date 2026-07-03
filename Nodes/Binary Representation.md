# Binary Representation

Aliases: binary encoding, biểu diễn nhị phân

Type: Computer Foundation

## Context / Ngữ cảnh

Binary Representation xuất hiện khi dữ liệu cần hiểu ở mức bit/byte: file, protocol, integer, flags hoặc machine-level storage.

## Boundary / Ranh giới

### Nó là gì

Binary Representation là cách biểu diễn value bằng bit 0/1 theo layout cụ thể.

### Nó không phải là gì

Nó không phải binary search và không nên dùng nếu text/schema format đã đủ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là mapping value sang bit pattern: base-2 notation, width, sign, byte order và field layout.

## Project Role / Vai trò trong dự án

Node này giúp debug protocol/file corruption, bit flag, numeric overflow hoặc low-level storage issue.

## Output / Artifact nên có

- Bit/byte layout cho field hoặc file/protocol
- Endian, signedness và width note
- Boundary test cho overflow, flag và byte order

## Decision Checklist / Câu hỏi kiểm tra

- Field này dùng bao nhiêu bit/byte?
- Byte order là little-endian hay big-endian?
- Bit pattern này là numeric value, flag set hay encoded data?

## Failure Modes / Cách nó gây lỗi

- Đọc sai endian làm value đảo nghĩa
- Signed/unsigned mismatch gây overflow
- Mask bit sai làm bật/tắt nhầm flag

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không làm protocol/file/low-level code
- Dễ over-engineer nếu dùng binary format khi text/schema format đủ rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Number System]] vì binary là hệ cơ số 2
- [[Data Representation]] vì binary là lớp biểu diễn thấp nhất

## Liên quan rộng

- Bit flags
- Byte layout

## Keywords / Từ khóa tìm kiếm

- Binary Representation
- bits and bytes
- binary encoding
- two complement
- machine representation
- biểu diễn nhị phân

## Source trace

- Computer Foundations Map Ch02-Ch03
