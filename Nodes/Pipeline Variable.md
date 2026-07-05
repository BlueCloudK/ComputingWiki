# Pipeline Variable

Aliases: Pipeline Variable, CI variable

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Pipeline Variable xuất hiện khi CI/CD workflow cần nhận cấu hình không nhạy cảm như environment, version, feature flag, path, image tag hoặc deploy mode.

## Boundary / Ranh giới

### Nó là gì

Pipeline Variable là biến cấu hình dùng trong pipeline để điều khiển build/test/deploy behavior.

### Nó không phải là gì

Pipeline Variable không phải secret. Credential, token, private key hoặc password phải nằm trong secret store và được xử lý như Pipeline Secret.

## Core Mechanism / Cơ chế lõi

Pipeline khai báo variable ở mức workflow/job/environment/repo/org. Job đọc variable qua environment/context, dùng nó trong condition, script, matrix hoặc deployment command.

## Project Role / Vai trò trong dự án

Dùng node này khi debug pipeline chạy sai môi trường, image tag sai, matrix build lệch, config drift giữa CI và local hoặc deploy dùng nhầm version.

## Output / Artifact nên có

- Variable name/purpose
- Scope and default value
- Allowed values/validation
- Producer/consumer job
- Difference from secret

## Decision Checklist / Câu hỏi kiểm tra

- Variable này có nhạy cảm không?
- Scope của variable là workflow, repo, org hay environment?
- Giá trị có enum/default rõ không?
- Job nào đọc variable này?
- Nếu thiếu hoặc sai thì pipeline fail sớm không?

## Failure Modes / Cách nó gây lỗi

- Dùng variable thường để chứa secret.
- Variable scope quá rộng làm job không liên quan bị ảnh hưởng.
- Không validate input làm deploy sai environment.
- Default value cũ làm pipeline chạy version sai.
- Local config và pipeline variable drift.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ có thể dùng config inline tạm thời.
- Không nên tạo nhiều variable nếu chỉ dùng một lần và không có owner rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Pipeline Secret]] vì cần phân biệt variable thường với secret.
- [[CI]] vì variable điều khiển CI job.
- [[CD]] vì deploy behavior thường phụ thuộc variable.
- [[Config Drift]] vì variable khác nhau giữa môi trường gây drift.

## Liên quan rộng

- CI configuration
- Environment config
- Build matrix

## Keywords / Từ khóa tìm kiếm

- Pipeline Variable
- CI variable
- workflow variable
- environment variable
- pipeline config
- workflow input
- pipeline variable debugging

## Source trace

- GitHub Actions documentation
- Twelve-Factor App
