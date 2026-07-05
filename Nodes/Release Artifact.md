# Release Artifact

Aliases: Release Artifact, build artifact

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Release Artifact xuất hiện khi CI/CD cần một output bất biến để deploy, rollback, audit và trace từ source code tới production.

## Boundary / Ranh giới

### Nó là gì

Release Artifact là file/image/package đã build và sẵn sàng phát hành, ví dụ container image, JAR, ZIP, binary, APK/AAB hoặc static bundle.

### Nó không phải là gì

Release Artifact không phải source code working tree. Không nên rebuild tùy ý ở production nếu muốn trace và rollback rõ.

## Core Mechanism / Cơ chế lõi

CI build artifact từ commit cụ thể, gắn version/digest, lưu vào artifact repository hoặc registry, rồi CD promote artifact đó qua environment.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế release pipeline, rollback, artifact signing, versioning hoặc trace lỗi production về commit.

## Output / Artifact nên có

- Artifact name/version/digest
- Source commit SHA
- Build metadata
- Storage location
- Promotion/rollback rule

## Decision Checklist / Câu hỏi kiểm tra

- Artifact có trace được về commit không?
- Artifact có immutable không?
- Environment nào đang chạy version nào?
- Rollback dùng artifact cũ hay rebuild?
- Artifact được lưu bao lâu?

## Failure Modes / Cách nó gây lỗi

- Rebuild cùng version nhưng nội dung khác.
- Artifact không trace được về commit.
- Artifact bị xóa trước khi cần rollback.
- Deploy dùng artifact local không qua pipeline.
- Version tag như `latest` làm production khó audit.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype local chưa deploy có thể chưa cần artifact repository formal.
- Không nên thêm signing/promotion phức tạp trước khi release flow ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CD]] vì CD promote release artifact qua environment.
- [[Artifact Repository]] vì artifact cần nơi lưu trữ và truy xuất.
- [[Rollback]] vì rollback thường cần artifact version cũ.
- [[Deployment]] vì deployment dùng artifact đã build.

## Liên quan rộng

- Release pipeline
- Versioning
- Supply chain

## Keywords / Từ khóa tìm kiếm

- Release Artifact
- build artifact
- artifact version
- container image digest
- immutable artifact
- release artifact debugging

## Source trace

- Continuous Delivery
- GitHub Actions documentation
