# Pipeline Secret

Aliases: Pipeline Secret, CI secret

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Pipeline Secret xuất hiện khi CI/CD workflow cần credential nhạy cảm để build, test, publish artifact, deploy hoặc gọi cloud/provider API.

## Boundary / Ranh giới

### Nó là gì

Pipeline Secret là secret được lưu và inject vào pipeline runtime, ví dụ token, cloud credential, registry password, signing key hoặc webhook secret.

### Nó không phải là gì

Pipeline Secret không phải environment variable bình thường để commit hoặc log. Nó phải có scope, rotation, masking và permission rõ.

## Core Mechanism / Cơ chế lõi

CI/CD platform lưu secret ở secret store, workflow request secret theo context được phép, inject vào job runtime và mask trong log. Secret nên chỉ có quyền tối thiểu cho job cần dùng.

## Project Role / Vai trò trong dự án

Dùng node này khi debug deploy/publish fail, credential expired, secret leak, fork PR permission, environment protection hoặc cloud access trong pipeline.

## Output / Artifact nên có

- Secret name/purpose
- Scope: repo/org/environment
- Permission policy
- Rotation owner/date
- Usage audit in workflow

## Decision Checklist / Câu hỏi kiểm tra

- Secret này dùng cho job nào?
- Quyền có nhỏ nhất có thể không?
- Secret có bị expose cho fork/untrusted workflow không?
- Có rotation plan không?
- Log có thể lộ secret qua echo/error không?

## Failure Modes / Cách nó gây lỗi

- Secret scope quá rộng làm blast radius lớn.
- Secret bị log ra qua command/debug output.
- Fork PR không có secret nên job fail khó hiểu.
- Credential hết hạn làm deploy fail.
- Một secret dùng chung quá nhiều môi trường nên khó rotate.

## Khi nào chưa cần hoặc dễ over-engineer

- Job không cần credential thì không nên cấp secret.
- Không nên dùng long-lived static secret nếu OIDC/short-lived credential đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Secret]] vì pipeline secret là một dạng secret vận hành.
- [[CI]] vì secret thường được inject vào CI job.
- [[CD]] vì deploy/publish cần credential nhạy cảm.
- [[Least Privilege]] vì secret nên có scope quyền tối thiểu.

## Liên quan rộng

- Credential management
- Secret rotation
- CI/CD security

## Keywords / Từ khóa tìm kiếm

- Pipeline Secret
- CI secret
- GitHub Actions secret
- deployment credential
- secret masking
- secret rotation
- pipeline secret debugging

## Source trace

- GitHub Actions documentation
- OWASP guidance
