# Dynamic Typing

Aliases: dynamically typed, kiểu động

Type: Computer Foundation

## Context / Ngữ cảnh

Dynamic Typing xuất hiện khi type compatibility được kiểm tra chủ yếu trong lúc chương trình chạy. Nó thường giúp code linh hoạt nhanh nhưng đẩy một số lỗi sang runtime.

## Boundary / Ranh giới

### Nó là gì

Dynamic Typing là typing strategy trong đó value mang type runtime và operation sai type thường chỉ lỗi khi execution đi tới đoạn đó.

### Nó không phải là gì

Nó không có nghĩa là language không có type, không đồng nghĩa với code bừa bãi, và không loại bỏ nhu cầu contract/test cho boundary.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là kiểm tra operation dựa trên value tại runtime: object có method/field không, value có hỗ trợ operator không, conversion xảy ra thế nào và error được raise khi nào.

## Project Role / Vai trò trong dự án

Dynamic Typing hữu ích cho scripting, prototyping và domain có shape dữ liệu linh hoạt. Trong project lớn, nó cần test, validation và convention tốt để tránh lỗi chỉ lộ ở production path hiếm.

## Output / Artifact nên có

- Runtime validation cho boundary nhận dữ liệu ngoài
- Test coverage cho path quan trọng và edge shape
- Convention về object shape, error handling hoặc optional field

## Decision Checklist / Câu hỏi kiểm tra

- Lỗi type có thể lộ ở path nào khi runtime?
- Boundary nào cần schema/validation rõ?
- Test đã cover shape dữ liệu quan trọng chưa?
- Có đang dựa vào duck typing một cách có kiểm soát không?
- Error message runtime có đủ rõ để debug không?

## Failure Modes / Cách nó gây lỗi

- Path ít chạy mới lộ type mismatch
- Object shape thay đổi nhưng không có contract/test bắt lại
- Runtime conversion ngầm làm data sai lặng lẽ
- Refactor rename field/method không bị phát hiện sớm

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần thêm type layer nặng nếu script nhỏ và input kiểm soát được
- Dễ over-engineer nếu cố biến dynamic code thành static model giả không cần thiết

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Type System]] vì dynamic typing vẫn là một chiến lược type checking
- [[Runtime]] vì dynamic type checks xảy ra khi chương trình chạy
- [[Validation]] vì boundary của dynamic code thường cần rule kiểm tra rõ
- [[Test Coverage]] vì test là lớp bảo vệ chính cho runtime-only type bugs

## Liên quan rộng

- Duck typing
- Runtime errors
- Schema validation

## Keywords / Từ khóa tìm kiếm

- Dynamic Typing
- runtime type checking
- duck typing
- dynamic language
- type error at runtime
- kiểu động

## Source trace

- Types and Programming Languages
- ACM/IEEE Computing Curricula 2020
