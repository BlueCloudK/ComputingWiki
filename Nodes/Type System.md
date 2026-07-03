# Type System

Aliases: typing system, hệ thống kiểu

Type: Computer Foundation

## Context / Ngữ cảnh

Type System xuất hiện khi language cần phân loại value/expression để phát hiện lỗi, giới hạn operation hợp lệ và giúp người đọc hiểu contract của code.

## Boundary / Ranh giới

### Nó là gì

Type System là tập rule gán type cho expression/value và kiểm tra operation nào được phép trên type đó.

### Nó không phải là gì

Nó không phải chỉ là annotation trong code, không đảm bảo business correctness, và không thay thế validation dữ liệu từ bên ngoài hệ thống.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là ràng buộc operation theo type: function nhận gì, trả gì, value nào có thể null/mutable, generic nào được áp dụng. Rule có thể được kiểm tra trước khi chạy hoặc trong runtime.

## Project Role / Vai trò trong dự án

Type System giúp encode domain constraint và API contract ngay trong code. Nó giảm một số bug integration/refactor, nhưng cũng có thể làm abstraction nặng nếu type phức tạp hơn problem.

## Output / Artifact nên có

- Type/interface/model mô tả dữ liệu quan trọng
- Boundary type cho API, module hoặc domain object
- Note về rule nullability, generics, mutability hoặc variance nếu ảnh hưởng design

## Decision Checklist / Câu hỏi kiểm tra

- Type này đang bảo vệ invariant nào?
- Lỗi nên được bắt ở compile-time hay runtime?
- Có đang dùng type để che business rule thật không?
- Boundary nhận dữ liệu untrusted có validation riêng chưa?
- Type abstraction có làm code dễ refactor hơn không?

## Failure Modes / Cách nó gây lỗi

- Tin type quá mức rồi bỏ validation input
- Dùng type quá rộng làm mất meaning của domain
- Dùng type quá phức tạp khiến code khó đọc/debug
- Runtime data không khớp type assumption ở boundary

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần type modeling sâu cho script nhỏ hoặc spike ngắn
- Dễ over-engineer nếu tạo nhiều generic/type layer mà không bảo vệ invariant thật

## Gồm những gì

- [[Static Typing]]
- [[Dynamic Typing]]

## Nối mạnh

- [[Programming Language]] vì type system là một phần quan trọng của language design
- [[Semantics]] vì type rule góp phần xác định chương trình có nghĩa hợp lệ không
- [[API Contract]] vì type thường biểu diễn request/response hoặc module boundary

## Liên quan rộng

- Domain modeling
- Refactoring safety
- Data validation

## Keywords / Từ khóa tìm kiếm

- Type System
- typing system
- hệ thống kiểu
- type
- system
- Computer Foundation
- hệ thống
- kiến trúc hệ thống
- ngôn ngữ lập trình

## Source trace

- Types and Programming Languages
- ACM/IEEE Computing Curricula 2020
