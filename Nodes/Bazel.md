# Bazel

Aliases: Bazel

Type: Frameworks and Tools

## Context / Ngữ cảnh

Bazel xuất hiện khi repo lớn hoặc monorepo cần build/test nhanh, reproducible và kiểm soát dependency graph rõ.

## Boundary / Ranh giới

### Nó là gì

Bazel là build system dựa trên target, rule và dependency graph. Nó tập trung vào hermetic build, cache và parallel execution.

### Nó không phải là gì

Bazel không phải package manager chung cho mọi ecosystem. Nó thường cần rule/config riêng để hiểu từng ngôn ngữ và artifact.

## Core Mechanism / Cơ chế lõi

Project khai báo target và dependency trong BUILD files. Bazel tính graph, chạy action cần thiết, dùng cache nếu input không đổi và tạo output reproducible.

## Project Role / Vai trò trong dự án

Dùng node này khi debug monorepo build, cache miss, dependency graph, CI build time hoặc multi-language build.

## Output / Artifact nên có

- BUILD files
- Target naming convention
- Rule/dependency map
- Cache strategy
- CI command

## Decision Checklist / Câu hỏi kiểm tra

- Target build/test là gì?
- Dependency có khai báo explicit không?
- Cache hit/miss có hợp lý không?
- Local và CI có dùng cùng config không?

## Failure Modes / Cách nó gây lỗi

- Dependency thiếu làm build chỉ fail trên clean machine.
- Rule quá phức tạp khó maintain.
- Cache key/input sai làm output stale.
- Monorepo build chậm vì graph chia chưa tốt.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo nhỏ, một ngôn ngữ, build đơn giản thường chưa cần Bazel.
- Không nên thêm Bazel nếu team chưa đủ nhu cầu monorepo/cache lớn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Build Cache]] vì Bazel phụ thuộc mạnh vào cache và input tracking.
- [[CI]] vì Bazel thường dùng để tăng tốc build/test trong CI.
- [[Matrix Build]] vì monorepo CI có thể chạy target theo matrix.

## Liên quan rộng

- Monorepo
- Reproducible build
- Build graph

## Keywords / Từ khóa tìm kiếm

- Bazel
- BUILD file
- build graph
- hermetic build
- remote cache
- Bazel debugging

## Source trace

- Bazel documentation
