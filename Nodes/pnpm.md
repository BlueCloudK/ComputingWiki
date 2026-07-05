# pnpm

Aliases: pnpm

Type: Frameworks and Tools

## Context / Ngữ cảnh

pnpm xuất hiện khi JavaScript project cần quản lý dependency nhanh, tiết kiệm dung lượng và reproducible hơn, đặc biệt trong monorepo hoặc nhiều project cùng máy/CI.

## Boundary / Ranh giới

### Nó là gì

pnpm là package manager cho JavaScript. Nó dùng content-addressable store và link để tránh copy package lặp lại, đồng thời dùng lockfile để pin dependency tree.

### Nó không phải là gì

pnpm không phải runtime JavaScript và không thay thế npm registry. Nó cũng không tự giải quyết security nếu dependency/version policy yếu.

## Core Mechanism / Cơ chế lõi

pnpm đọc `package.json`, resolve dependency, ghi `pnpm-lock.yaml`, tải package vào store chung và tạo `node_modules` bằng link. CI thường dùng frozen lockfile để tránh drift.

## Project Role / Vai trò trong dự án

Dùng node này khi debug install fail, workspace, peer dependency, lockfile drift, CI cache hoặc dependency local không resolve đúng.

## Output / Artifact nên có

- `package.json`
- `pnpm-lock.yaml`
- `pnpm-workspace.yaml` nếu là monorepo
- pnpm version policy
- CI install command

## Decision Checklist / Câu hỏi kiểm tra

- Repo có dùng pnpm là package manager chính không?
- Lockfile có được commit không?
- CI có dùng frozen lockfile không?
- Workspace package có link đúng không?
- Store/cache có làm install dùng dependency cũ không?

## Failure Modes / Cách nó gây lỗi

- Quên commit lockfile làm install lệch giữa máy.
- Peer dependency conflict làm runtime lỗi.
- CI dùng npm/yarn nhầm với repo pnpm.
- Workspace link sai làm package local không resolve.
- Cache store cũ làm debug install khó.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ đã ổn với npm có thể chưa cần đổi.
- Không nên đổi package manager khi team/tooling chưa thống nhất.
- Không nên dùng workspace nếu repo chỉ có một package đơn giản.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[npm]] vì pnpm giải quyết cùng vùng package management JavaScript.
- [[JavaScript]] vì pnpm quản lý dependency cho JavaScript ecosystem.
- [[Dependency Resolver]] vì pnpm cần resolve dependency graph và lockfile.
- [[CI]] vì CI cần install dependency reproducibly.
- [[Build Cache]] vì pnpm store/cache ảnh hưởng tốc độ pipeline.

## Liên quan rộng

- Package management
- Monorepo
- Dependency install
- JavaScript tooling

## Keywords / Từ khóa tìm kiếm

- pnpm
- pnpm-lock.yaml
- pnpm workspace
- package manager
- frozen lockfile
- content-addressable store
- pnpm install
- pnpm debugging

## Source trace

- pnpm documentation
- npm documentation
