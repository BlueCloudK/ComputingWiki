# Frameworks and Tools

Aliases: developer tooling, build tools, package tools, công cụ phát triển

Type: MOC

## Context / Ngữ cảnh

Frameworks and Tools gom các công cụ ổn định quanh version control, package management, build, test, lint, release và local development.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC điều hướng cho các node thuộc Frameworks and Tools.

### Nó không phải là gì

Nó không phải tutorial dài hoặc danh sách tool rời rạc.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom node theo workflow, artifact, runtime behavior và failure mode.

## Project Role / Vai trò trong dự án

MOC này giúp mở rộng ComputingWiki có kiểm soát và tìm đúng vùng khi làm project.

## Output / Artifact nên có

- Pack map
- Navigation links
- Source trace cấp vùng

## Decision Checklist / Câu hỏi kiểm tra

- Node có thuộc pack này thật không?
- Link có giúp navigation không?
- Node có nên là tool riêng hay chỉ là keyword?

## Failure Modes / Cách nó gây lỗi

- Nhồi tool quá nhiều mà thiếu cơ chế
- Link rộng làm graph nhiễu
- Node thiếu source trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần chia sâu nếu pack chưa được dùng trong path
- Dễ over-engineer nếu biến MOC thành tutorial

## Gồm những gì

- [[Git]]
- [[Repository Clone]]
- [[Git Commit]]
- [[Git Branch]]
- [[Git Merge]]
- [[Git Rebase]]
- [[Merge Conflict]]
- [[Pull Request]]
- [[Code Review Tool]]
- [[Git Tag]]
- [[Git Remote]]
- [[Git Fetch]]
- [[Git Pull]]
- [[Git Push]]
- [[Git Stash]]
- [[Git Ignore]]
- [[Git Submodule]]
- [[Semantic Release]]
- [[Conventional Commits]]
- [[Changelog Generation]]
- [[GitHub]]
- [[GitLab]]
- [[Bitbucket]]
- [[GitHub Actions Workflow]]
- [[CI Runner]]
- [[Package Lock File]]
- [[Dependency Lockfile]]
- [[npm]]
- [[pnpm]]
- [[Yarn]]
- [[Node Package Manager]]
- [[Maven]]
- [[Gradle]]
- [[NuGet]]
- [[Pip]]
- [[Poetry]]
- [[Cargo]]
- [[Go Modules]]
- [[Make]]
- [[Makefile]]
- [[CMake]]
- [[Bazel]]
- [[Webpack]]
- [[Vite]]
- [[Rollup]]
- [[esbuild]]
- [[Babel]]
- [[SWC]]
- [[ESLint]]
- [[Prettier]]
- [[Type Checker]]
- [[Formatter]]
- [[Linter]]
- [[Static Analyzer]]
- [[Unit Test Runner]]
- [[Test Reporter]]
- [[Coverage Reporter]]
- [[Mocking Framework]]
- [[Fixture Loader]]
- [[Snapshot Test]]
- [[Local Dev Server]]
- [[Hot Reload]]
- [[Live Reload]]
- [[Environment File]]
- [[Dotenv]]
- [[Dockerfile]]
- [[Dev Container]]
- [[Task Runner]]
- [[Scaffolding Tool]]
- [[CLI Tool]]
- [[SDK]]
- [[Library]]
- [[Framework]]
- [[Plugin]]
- [[Extension]]
- [[IDE]]
- [[Debugger Tool]]
- [[Profiler Tool]]
- [[Package Registry]]
- [[Artifact Cache]]
- [[Dependency Update Bot]]
- [[Release Notes Tool]]
- [[Documentation Generator]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application Engineering
- Deployment and Operations
- Programming Languages

## Keywords / Từ khóa tìm kiếm

- Frameworks and Tools
- developer tooling
- build tools
- package tools
- công cụ phát triển

## Source trace

- Git documentation
- GitHub Actions documentation
- npm documentation
- Maven documentation
- Gradle documentation
