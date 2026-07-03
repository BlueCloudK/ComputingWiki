# Static Typing

Aliases: statically typed, kiểu tĩnh

Type: Computer Foundation

## Context / Ngữ cảnh

Static Typing xuất hiện khi type của expression được kiểm tra trước khi chương trình chạy. Nó quan trọng trong refactor, API boundary và codebase lớn cần feedback sớm.

## Boundary / Ranh giới

### Nó là gì

Static Typing là typing strategy trong đó type rule được kiểm tra ở compile-time hoặc trước execution chính.

### Nó không phải là gì

Nó không tự động làm code đúng business logic, không thay thế test, và không đồng nghĩa với verbose syntax vì nhiều language có type inference.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là reject chương trình không thỏa type rule trước khi chạy. Compiler/type checker dùng annotation hoặc inference để phát hiện mismatch, missing member, invalid call hoặc incompatible return.

## Project Role / Vai trò trong dự án

Static Typing giúp refactor an toàn hơn và làm contract module rõ hơn. Nó rất hữu ích khi nhiều người sửa code hoặc API/data model thay đổi thường xuyên.

## Output / Artifact nên có

- Type/interface rõ cho boundary quan trọng
- Type check trong CI hoặc build pipeline
- Note về type escape hatch như any/cast nếu dùng

## Decision Checklist / Câu hỏi kiểm tra

- Type error này đang bắt bug thật hay chỉ do model type kém?
- Boundary nào cần type chặt nhất?
- Có đang lạm dụng cast/any để bỏ qua type system không?
- Type inference có đủ rõ cho người đọc không?
- Runtime validation đã có cho dữ liệu ngoài chưa?

## Failure Modes / Cách nó gây lỗi

- Tin compiler nên bỏ test behavior
- Dùng escape hatch làm type system mất giá trị
- Type model quá phức tạp khiến refactor sợ hơn
- Static type không phản ánh dữ liệu runtime thật từ API/user

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần type modeling sâu cho spike hoặc script throwaway
- Dễ over-engineer nếu mục tiêu chỉ là làm compiler hài lòng chứ không bảo vệ invariant

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Type System]] vì static typing là một chiến lược kiểm tra type
- [[Compiler]] vì compiler/type checker thường thực hiện static checks
- [[API Contract]] vì static type có thể encode request/response shape trong code

## Liên quan rộng

- Type inference
- Compile-time feedback
- Refactoring safety

## Keywords / Từ khóa tìm kiếm

- Static Typing
- compile time type checking
- type annotation
- type inference
- type safety
- static type error
- kiểu tĩnh

## Source trace

- Types and Programming Languages
- ACM/IEEE Computing Curricula 2020
