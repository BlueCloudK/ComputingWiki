# Dependency Resolver

Aliases: Dependency Resolver, dependency resolution

Type: Frameworks and Tools

## Context / Ngữ cảnh

Dependency Resolver xuất hiện khi package manager hoặc build tool phải chọn version dependency phù hợp giữa nhiều constraint khác nhau.

## Boundary / Ranh giới

### Nó là gì

Dependency Resolver là cơ chế tính dependency graph và chọn version/package thỏa constraint, lockfile, range, platform và conflict rule.

### Nó không phải là gì

Dependency Resolver không phải registry. Registry lưu package; resolver quyết định package/version nào sẽ được dùng.

## Core Mechanism / Cơ chế lõi

Resolver đọc manifest, version range, lockfile và dependency transitive. Nó chọn graph hợp lệ, ghi lockfile nếu cần, rồi package manager tải/cài graph đó.

## Project Role / Vai trò trong dự án

Dùng node này khi debug install fail, dependency conflict, lockfile drift, peer dependency, workspace hoặc build khác giữa local và CI.

## Output / Artifact nên có

- Dependency manifest
- Lockfile
- Conflict/error log
- Resolution override note nếu có
- CI install command

## Decision Checklist / Câu hỏi kiểm tra

- Version range có quá rộng không?
- Lockfile có là source of truth không?
- Conflict đến từ direct hay transitive dependency?
- Local và CI dùng cùng package manager/version không?
- Có override/resolution nào cần document không?

## Failure Modes / Cách nó gây lỗi

- Lockfile drift làm local khác CI.
- Transitive dependency kéo version lỗi.
- Peer dependency conflict bị bỏ qua.
- Override quá rộng che bug thật.
- Registry/cache khác nhau làm graph khác nhau.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không dependency ngoài thì chưa cần đào sâu resolver.
- Không nên dùng override nếu có thể upgrade package gốc rõ ràng hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[npm]] vì npm có resolver và lockfile riêng.
- [[pnpm]] vì pnpm resolution ảnh hưởng workspace/linking.
- [[Pip]] vì pip resolve Python dependency.
- [[Build Cache]] vì cache có thể che lỗi resolution.

## Liên quan rộng

- Package management
- Lockfile
- Dependency graph

## Keywords / Từ khóa tìm kiếm

- Dependency Resolver
- dependency resolution
- lockfile
- dependency conflict
- version range
- transitive dependency
- resolver debugging

## Source trace

- npm documentation
- pip documentation
- pnpm documentation
