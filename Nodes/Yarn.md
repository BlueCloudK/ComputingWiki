# Yarn

Aliases: Yarn

Type: Frameworks and Tools

## Context / Ngữ cảnh

Yarn xuất hiện khi JavaScript project cần package manager để cài dependency, chạy scripts, quản lý lockfile và hỗ trợ workspace.

## Boundary / Ranh giới

### Nó là gì

Yarn là package manager cho JavaScript ecosystem. Nó đọc `package.json`, resolve dependency, ghi lockfile và cài package theo version đã chọn.

### Nó không phải là gì

Yarn không phải runtime JavaScript và không thay thế npm registry. Nó cũng không tự đảm bảo dependency an toàn nếu version/lockfile/policy không rõ.

## Core Mechanism / Cơ chế lõi

Yarn resolve dependency graph từ manifest, lock version trong `yarn.lock`, cài package vào project/cache và chạy script như build/test/dev.

## Project Role / Vai trò trong dự án

Dùng node này khi debug install fail, lockfile drift, workspace, dependency conflict, CI cache hoặc script chạy khác local.

## Output / Artifact nên có

- `package.json`
- `yarn.lock`
- Yarn version policy
- Workspace config nếu có
- CI install command

## Decision Checklist / Câu hỏi kiểm tra

- Repo có dùng Yarn là package manager chính không?
- Lockfile có được commit không?
- CI có dùng đúng Yarn version không?
- Workspace package có resolve đúng không?
- Cache có làm install dùng dependency cũ không?

## Failure Modes / Cách nó gây lỗi

- CI dùng npm/pnpm nhầm với repo Yarn.
- Lockfile drift làm local khác CI.
- Workspace dependency resolve sai.
- Package manager version khác làm install behavior khác.
- Cache cũ che lỗi dependency thật.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ đã ổn với npm có thể chưa cần đổi.
- Không nên đổi package manager nếu team/tooling chưa thống nhất.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[npm]] vì Yarn giải quyết cùng vùng package management JavaScript.
- [[JavaScript]] vì Yarn quản lý dependency cho JavaScript project.
- [[Dependency Resolver]] vì Yarn cần resolve dependency graph.
- [[CI]] vì install dependency reproducibly là phần quan trọng của pipeline.
- [[Build Cache]] vì cache ảnh hưởng tốc độ và độ ổn định install.

## Liên quan rộng

- Package management
- JavaScript tooling
- Monorepo workspace

## Keywords / Từ khóa tìm kiếm

- Yarn
- yarn.lock
- Yarn workspace
- package manager
- dependency install
- yarn install
- Yarn debugging

## Source trace

- Yarn documentation
- npm documentation
