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

- Base conversion note cho binary/decimal/hex quan trọng
- Range/sign note cho field numeric trong protocol/file
- Boundary test cho parsing hoặc conversion số

## Decision Checklist / Câu hỏi kiểm tra

- Giá trị này đang ở base nào khi đọc/ghi/log?
- Có signed/unsigned hoặc width constraint không?
- Conversion qua string/JSON/binary có làm đổi nghĩa không?

## Failure Modes / Cách nó gây lỗi

- Nhầm hex/binary/decimal khi đọc payload
- Overflow hoặc truncation vì không ghi range
- Log hiển thị decimal nhưng protocol dùng bit field

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu chỉ xử lý số business ở tầng app
- Dễ over-engineer nếu đào bit-level khi lỗi nằm ở validation/domain rule

## Gồm những gì

- [[Binary Representation]]

## Nối mạnh

- [[Data Representation]] vì number system là một phần của cách máy biểu diễn dữ liệu

## Liên quan rộng

- Hexadecimal
- Integer representation

## Keywords / Từ khóa tìm kiếm

- Number System
- binary decimal hexadecimal
- base conversion
- positional notation
- hệ đếm

## Source trace

- Computer Foundations Map Ch02
