# Package Registry

Aliases: Package Registry, package registry

Type: Frameworks and Tools

## Context / Ngữ cảnh

Package Registry xuất hiện khi project cần publish, resolve, download và audit dependency/package theo version, scope, owner và access policy.

## Boundary / Ranh giới

### Nó là gì

Package Registry là dịch vụ lưu trữ package artifact và metadata version để package manager như npm, Maven, Gradle, Cargo hoặc NuGet có thể install/resolve dependency.

### Nó không phải là gì

Package Registry không phải dependency resolver. Registry giữ package/version; resolver quyết định version nào được chọn dựa trên manifest, lockfile và constraint.

## Core Mechanism / Cơ chế lõi

Package được publish với name, version, checksum, metadata và artifact. Package manager query registry, tải package theo resolved version, kiểm tra integrity và cache/local install nếu hợp lệ.

## Project Role / Vai trò trong dự án

Dùng node này khi debug install fail, private package, supply-chain risk, publish release, registry auth, package integrity hoặc CI dependency download chậm.

## Output / Artifact nên có

- Registry URL/scope config
- Package name/version
- Auth token/publish permission boundary
- Integrity/checksum metadata
- Retention/deprecation policy nếu internal registry

## Decision Checklist / Câu hỏi kiểm tra

- Package lấy từ public hay private registry?
- Scope/name có trỏ đúng registry không?
- Token có quyền install hay publish?
- Version artifact có immutable không?
- CI có dùng lockfile và integrity check không?

## Failure Modes / Cách nó gây lỗi

- Scope config sai làm tải package từ registry nhầm.
- Token hết hạn hoặc quyền quá rộng.
- Package bị unpublish/deprecate làm build fail.
- Registry private down làm CI/deploy bị chặn.
- Không pin/lock version làm dependency supply chain drift.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ dùng public ecosystem có thể chưa cần private registry.
- Không nên tự host registry nếu chưa có nhu cầu access control, caching hoặc artifact retention rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[npm]] vì npm dùng package registry cho JavaScript package.
- [[Dependency Resolver]] vì resolver lấy metadata/version từ registry.
- [[Artifact Repository]] vì package registry là một dạng artifact repository.
- [[CI]] vì pipeline thường install package từ registry.

## Liên quan rộng

- Dependency management
- Package publishing
- Supply chain security

## Keywords / Từ khóa tìm kiếm

- Package Registry
- package registry
- private registry
- package publish
- registry auth
- package integrity
- package registry debugging

## Source trace

- npm documentation
- Maven documentation
- Gradle documentation
- NuGet documentation
