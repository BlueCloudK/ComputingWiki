# Number System

Aliases: numeric representation, hệ đếm

Type: Computer Foundation

## Context / Ngữ cảnh

Number System xuất hiện khi cần hiểu số được biểu diễn bằng binary, decimal, hex hoặc base khác.

## Boundary / Ranh giới

### Nó là gì

Number System là cách biểu diễn số bằng base, chữ số và positional value.

### Nó không phải là gì

Nó không phải business arithmetic và không tự giải thích toàn bộ floating-point precision.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là positional notation: giá trị của chữ số phụ thuộc vị trí và base.

## Project Role / Vai trò trong dự án

Node này giúp đọc binary/hex, bit flag, protocol field và low-level data representation.

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

- [[Binary Representation]]

## Nối mạnh

- [[Data Representation]] vì number system là một phần của cách máy biểu diễn dữ liệu

## Liên quan rộng

- Hexadecimal
- Integer representation

## Source trace

- Computer Foundations Map Ch02
