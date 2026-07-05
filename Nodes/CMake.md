# CMake

Aliases: CMake

Type: Frameworks and Tools

## Context / Ngữ cảnh

CMake xuất hiện khi C/C++ hoặc native project cần build trên nhiều platform, compiler và IDE khác nhau.

## Boundary / Ranh giới

### Nó là gì

CMake là meta-build system. Nó đọc config trong `CMakeLists.txt` rồi sinh build files cho Ninja, Makefile, Visual Studio hoặc toolchain khác.

### Nó không phải là gì

CMake không phải compiler. Nó điều phối compiler, linker, target, dependency và build option.

## Core Mechanism / Cơ chế lõi

Project khai báo target, source, include path, library, option và dependency. CMake configure project rồi generate build system cụ thể. Sau đó build tool thật compile/link artifact.

## Project Role / Vai trò trong dự án

Dùng node này khi debug native build, library link, cross-platform compile, toolchain file hoặc dependency native.

## Output / Artifact nên có

- `CMakeLists.txt`
- Target/library structure
- Toolchain/build preset
- Build output path
- Link/dependency note

## Decision Checklist / Câu hỏi kiểm tra

- Target nào tạo executable/library?
- Compiler/toolchain là gì?
- Include/library path có đúng không?
- Build Debug/Release có khác gì?
- Dependency native resolve ở đâu?

## Failure Modes / Cách nó gây lỗi

- Link library thiếu hoặc sai thứ tự.
- Include path sai làm compile fail.
- Debug/Release config lệch.
- Toolchain file sai khi cross-compile.
- Build cache/config cũ làm lỗi khó hiểu.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không có native build thì chưa cần CMake.
- Không nên thêm CMake nếu build tool đơn giản hiện tại đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ABI]] vì native build cần binary compatibility.
- [[Linker]] vì CMake cấu hình link target/library.
- [[Build Cache]] vì native build thường có cache/config output.
- [[CI]] vì native build cần chạy trong pipeline.

## Liên quan rộng

- Native build
- C/C++ tooling
- Cross-platform compile

## Keywords / Từ khóa tìm kiếm

- CMake
- CMakeLists.txt
- native build
- build target
- toolchain file
- linker
- CMake debugging

## Source trace

- CMake documentation
