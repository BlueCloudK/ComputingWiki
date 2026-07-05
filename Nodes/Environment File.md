# Environment File

Aliases: Environment File, env file, dotenv file

Type: Frameworks and Tools

## Context / Ngữ cảnh

Environment File xuất hiện khi project cần lưu cấu hình môi trường local/dev/test như API URL, feature flag, port, mode hoặc non-secret config theo dạng file.

## Boundary / Ranh giới

### Nó là gì

Environment File là file cấu hình biến môi trường, thường như `.env`, được app/tool đọc để set config runtime/build-time.

### Nó không phải là gì

Environment File không phải nơi an toàn để commit secret. Token, password, private key và production credential nên nằm trong secret manager hoặc CI/CD secret store.

## Core Mechanism / Cơ chế lõi

Tool/runtime đọc key-value từ file env, inject vào process hoặc build config. App đọc config qua environment variable hoặc config layer, thường có file mẫu `.env.example` để document key cần có.

## Project Role / Vai trò trong dự án

Dùng node này khi setup local dev, debug config sai môi trường, tách dev/staging/prod, hoặc kiểm tra nguy cơ lộ secret trong repo.

## Output / Artifact nên có

- `.env.example`
- Env key schema/description
- Ignore rule cho `.env` thật
- Runtime/build-time boundary note
- Secret handling policy

## Decision Checklist / Câu hỏi kiểm tra

- Key nào là config thường, key nào là secret?
- `.env` thật có bị git ignore không?
- `.env.example` có đủ key bắt buộc không?
- Biến này được đọc ở runtime hay build-time?
- CI/staging/prod lấy config từ đâu?

## Failure Modes / Cách nó gây lỗi

- Commit nhầm secret vào repo.
- Local `.env` khác CI làm bug chỉ xuất hiện khi deploy.
- Build-time env bị nhầm với runtime env.
- Key thiếu default/validation làm app crash muộn.
- `.env.example` stale khiến người mới setup lỗi.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ có thể dùng config inline tạm thời.
- Không nên tạo nhiều env file nếu boundary môi trường chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Environment Variable]] vì env file là cách khai báo environment variable.
- [[Secret]] vì file env dễ lẫn secret và cần policy rõ.
- [[Config Drift]] vì env khác nhau giữa môi trường gây drift.
- [[CI]] vì CI cần inject config/secret khác local.

## Liên quan rộng

- Dotenv
- Local development config
- Runtime configuration

## Keywords / Từ khóa tìm kiếm

- Environment File
- env file
- dotenv
- .env
- .env.example
- environment config
- env file debugging

## Source trace

- Twelve-Factor App
- dotenv documentation
