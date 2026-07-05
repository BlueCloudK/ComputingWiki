# Artifact Repository

Aliases: Artifact Repository, artifact registry

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Artifact Repository xuất hiện khi team cần nơi lưu package, container image, binary hoặc release artifact để CI/CD lấy lại một cách ổn định.

## Boundary / Ranh giới

### Nó là gì

Artifact Repository là kho lưu trữ artifact đã build, có version, metadata, access control và retention policy.

### Nó không phải là gì

Artifact Repository không phải source repository. Source repo lưu code; artifact repo lưu output build.

## Core Mechanism / Cơ chế lõi

CI publish artifact vào repository với version/digest. CD, developer hoặc runtime pull artifact theo version cụ thể. Repository quản lý permission, retention, cache và metadata.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế package registry, container registry, release retention, rollback hoặc supply-chain trace.

## Output / Artifact nên có

- Repository/registry location
- Artifact naming/versioning convention
- Access control rule
- Retention policy
- Promotion rule

## Decision Checklist / Câu hỏi kiểm tra

- Artifact loại gì được lưu ở đây?
- Ai được publish và ai được pull?
- Version có immutable không?
- Retention có giữ đủ cho rollback không?
- Artifact có scan/sign/metadata không?

## Failure Modes / Cách nó gây lỗi

- Artifact bị overwrite cùng version.
- Retention xóa artifact rollback.
- Permission quá rộng làm publish nhầm.
- CI publish vào registry khác CD đang dùng.
- Tag mơ hồ làm deploy sai version.

## Khi nào chưa cần hoặc dễ over-engineer

- Project chưa release/deploy có thể chưa cần artifact repository riêng.
- Không nên tạo nhiều registry nếu một registry rõ boundary đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Release Artifact]] vì artifact repository lưu release artifact.
- [[CD]] vì CD pull artifact từ repository để deploy.
- [[Secret]] vì registry credential là secret cần bảo vệ.
- [[Least Privilege]] vì publish/pull permission cần scope nhỏ.

## Liên quan rộng

- Package registry
- Container registry
- Release management

## Keywords / Từ khóa tìm kiếm

- Artifact Repository
- artifact registry
- package registry
- container registry
- artifact retention
- artifact version
- artifact repository debugging

## Source trace

- GitHub Packages documentation
- Continuous Delivery
