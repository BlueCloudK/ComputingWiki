# ABI

Aliases: ABI, Application Binary Interface

Type: Programming Languages Deep

## Context / Ngữ cảnh

ABI xuất hiện khi compiled code, native library, operating system hoặc language runtime cần tương thích ở mức binary.

## Boundary / Ranh giới

### Nó là gì

ABI là contract ở mức binary: calling convention, register usage, stack layout, symbol naming, data layout và cách truyền/nhận value giữa compiled components.

### Nó không phải là gì

ABI không giống API source-level. API nói code gọi gì; ABI nói binary đã compile gọi nhau như thế nào.

## Core Mechanism / Cơ chế lõi

Compiler tạo binary theo ABI của platform. Khi program gọi library, cả hai bên phải thống nhất function signature, calling convention, memory layout, symbol và linking rule.

## Project Role / Vai trò trong dự án

Dùng node này khi debug native crash, FFI, shared library, mobile native module, linker error hoặc dependency binary không tương thích.

## Output / Artifact nên có

- Target platform/architecture note
- Calling convention note nếu cần
- Library version and symbol compatibility
- Build/link config
- Test trên target runtime thật

## Decision Checklist / Câu hỏi kiểm tra

- Binary target architecture là gì?
- Library được build bằng ABI nào?
- Function signature có khớp không?
- Version native dependency có tương thích không?
- Crash có chỉ xảy ra trên một platform/architecture không?

## Failure Modes / Cách nó gây lỗi

- Library build sai architecture.
- Calling convention mismatch.
- Struct/layout khác giữa hai bên.
- Symbol không tìm thấy khi link/load.
- Crash chỉ xảy ra trên một platform cụ thể.

## Khi nào chưa cần hoặc dễ over-engineer

- Code thuần managed/runtime cao có thể chưa cần quan tâm ABI.
- Không nên đụng ABI nếu không có native/FFI/binary dependency.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[FFI]] vì FFI phụ thuộc ABI đúng.
- [[Linker]] vì linker cần symbol và binary compatibility.
- [[Runtime]] vì ABI ảnh hưởng cách binary chạy trong runtime/platform.
- [[Memory Management]] vì layout/ownership sai có thể gây memory bug.

## Liên quan rộng

- Native code
- Binary compatibility
- Compiler toolchain

## Keywords / Từ khóa tìm kiếm

- ABI
- Application Binary Interface
- calling convention
- binary compatibility
- symbol
- struct layout
- native library
- ABI debugging

## Source trace

- LLVM documentation
- System V ABI references
