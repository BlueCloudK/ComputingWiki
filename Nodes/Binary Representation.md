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

- [[Number System]] vì binary là hệ cơ số 2
- [[Data Representation]] vì binary là lớp biểu diễn thấp nhất

## Liên quan rộng

- Bit flags
- Byte layout

## Source trace

- Computer Foundations Map Ch02-Ch03
