# FFI

Aliases: FFI, Foreign Function Interface

Type: Programming Languages Deep

## Context / Ngữ cảnh

FFI xuất hiện khi một ngôn ngữ cần gọi code hoặc thư viện viết bằng ngôn ngữ khác, thường là native library như C/C++/Rust.

## Boundary / Ranh giới

### Nó là gì

FFI là cơ chế cho phép runtime/ngôn ngữ này gọi function, truyền dữ liệu hoặc nhận callback từ thư viện/ngôn ngữ khác.

### Nó không phải là gì

FFI không phải API network. Nó chạy trong cùng process hoặc boundary native gần hơn, nên lỗi có thể ảnh hưởng memory, crash và security.

## Core Mechanism / Cơ chế lõi

Code gọi qua binding khai báo function signature, type mapping, memory ownership và calling convention. Runtime chuyển data qua boundary rồi nhận kết quả hoặc error.

## Project Role / Vai trò trong dự án

Dùng node này khi debug native module, mobile bridge, Python/Rust/C interop, performance wrapper hoặc crash ở boundary native.

## Output / Artifact nên có

- Binding/interface definition
- Type mapping note
- Memory ownership rule
- Error handling convention
- Test qua boundary native

## Decision Checklist / Câu hỏi kiểm tra

- Function signature có khớp native library không?
- Ai sở hữu memory được truyền qua boundary?
- ABI/calling convention có đúng không?
- Error native được map về runtime thế nào?

## Failure Modes / Cách nó gây lỗi

- Type mapping sai làm crash.
- Memory ownership sai gây leak hoặc use-after-free.
- ABI mismatch làm behavior khó đoán.
- Native error không được map rõ.

## Khi nào chưa cần hoặc dễ over-engineer

- Nếu có pure library trong cùng ecosystem thì chưa cần FFI.
- Không nên dùng FFI chỉ để tối ưu sớm khi bottleneck chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ABI]] vì FFI phụ thuộc binary interface và calling convention.
- [[Runtime]] vì FFI đi qua boundary runtime/native.
- [[Memory Management]] vì ownership qua FFI rất dễ lỗi.

## Liên quan rộng

- Native interop
- Language runtime
- Mobile bridge

## Keywords / Từ khóa tìm kiếm

- FFI
- Foreign Function Interface
- native binding
- language interop
- calling convention
- memory ownership
- FFI debugging

## Source trace

- LLVM documentation
- Rust FFI documentation
