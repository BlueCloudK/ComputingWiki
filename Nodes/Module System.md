# Module System

Aliases: Module System, module system

Type: Programming Languages Deep

## Context / Ngữ cảnh

Module System xuất hiện khi ngôn ngữ hoặc runtime cần chia code thành unit có import/export, namespace, dependency và visibility rõ.

## Boundary / Ranh giới

### Nó là gì

Module System là cơ chế tổ chức code thành module/package/file/library, quy định cách khai báo dependency, expose API và resolve symbol giữa các phần code.

### Nó không phải là gì

Module System không giống package manager. Package manager tải/cài dependency; module system quyết định code import/export và được load/linked như thế nào.

## Core Mechanism / Cơ chế lõi

Compiler/runtime đọc import/export, resolve module path/name, kiểm tra visibility hoặc type nếu có, rồi load/link module theo rule như static, dynamic, ESM, CommonJS hoặc language-specific module system.

## Project Role / Vai trò trong dự án

Dùng node này khi debug import lỗi, circular dependency, public/private API boundary, build output module format hoặc refactor architecture theo module.

## Output / Artifact nên có

- Module/package boundary map
- Public API/export list
- Dependency direction rule
- Module format/config note
- Circular dependency check

## Decision Checklist / Câu hỏi kiểm tra

- Module này expose API nào?
- Dependency direction có bị ngược không?
- Có circular import không?
- Runtime/build tool dùng module format nào?
- Internal implementation có bị export quá rộng không?

## Failure Modes / Cách nó gây lỗi

- Circular dependency làm init order lỗi.
- Export quá rộng làm boundary kiến trúc bị phá.
- ESM/CJS hoặc module format mismatch.
- Path alias khác giữa IDE/test/build.
- Package manager cài đúng nhưng runtime resolve sai module.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ một file chưa cần module boundary phức tạp.
- Không nên tách module theo tên đẹp nếu dependency direction chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì JavaScript có ESM/CommonJS module system quan trọng.
- [[Linker]] vì compiled language có module/linking boundary.
- [[Build Tool]] vì build tool thường resolve/transpile module.
- [[Dependency Resolver]] vì dependency package khác module import nhưng thường liên quan.

## Liên quan rộng

- Import export
- Namespace
- Package boundary
- Circular dependency

## Keywords / Từ khóa tìm kiếm

- Module System
- module system
- import export
- module resolution
- ESM
- CommonJS
- circular dependency
- module system debugging

## Source trace

- ECMAScript documentation
- Crafting Interpreters
- Engineering a Compiler
