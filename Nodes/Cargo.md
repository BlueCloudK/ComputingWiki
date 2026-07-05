# Cargo

Aliases: Cargo, Rust Cargo

Type: Frameworks and Tools

## Context / Ngữ cảnh

Cargo xuất hiện khi Rust project cần quản lý dependency, build, test, package và publish crate.

## Boundary / Ranh giới

### Nó là gì

Cargo là package manager và build tool chính của Rust ecosystem.

### Nó không phải là gì

Cargo không phải Rust compiler trực tiếp. Compiler chính là `rustc`, còn Cargo điều phối build/dependency/test.

## Core Mechanism / Cơ chế lõi

Cargo đọc `Cargo.toml` và `Cargo.lock`, resolve dependency, gọi compiler, chạy test/bench/doc và tạo artifact trong target directory.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Rust build, crate dependency, feature flag, workspace, test hoặc publish package.

## Output / Artifact nên có

- `Cargo.toml`
- `Cargo.lock`
- Feature/workspace note
- Build/test command
- Artifact output note

## Decision Checklist / Câu hỏi kiểm tra

- Package là binary hay library crate?
- Feature flag nào đang bật?
- Lockfile có commit không?
- Workspace dependency có đúng không?
- CI có chạy cargo test/build không?

## Failure Modes / Cách nó gây lỗi

- Feature flag thiếu làm compile path khác.
- Dependency version lệch.
- Workspace config sai làm package không resolve.
- Build cache cũ làm debug khó.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không dùng Rust thì chưa cần Cargo.
- Không nên tách workspace sớm nếu chỉ có một crate nhỏ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Rust]] vì Cargo là tool chính của Rust project.
- [[CI]] vì Rust build/test thường chạy qua Cargo trong pipeline.
- [[Build Cache]] vì target directory/cache ảnh hưởng tốc độ build.
- [[FFI]] vì Rust crate đôi khi expose native boundary.

## Liên quan rộng

- Rust ecosystem
- Package management
- Build tooling

## Keywords / Từ khóa tìm kiếm

- Cargo
- Rust Cargo
- Cargo.toml
- Cargo.lock
- cargo build
- cargo test
- Rust crate
- Cargo debugging

## Source trace

- Rust Cargo Book
