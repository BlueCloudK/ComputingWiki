# Environment Variable

Aliases: env var, biến môi trường

Type: Deployment / Operations

## Context / Ngữ cảnh

Environment Variable xuất hiện khi app cần nhận config từ môi trường chạy thay vì hard-code trong source code. Nó thường dùng cho port, database URL, API endpoint, feature flag, log level, runtime mode, secret reference hoặc deployment-specific settings giữa dev/staging/production.

## Boundary / Ranh giới

### Nó là gì

Environment Variable là key-value được runtime/process/container cung cấp cho application. Nó giúp cùng một artifact chạy ở nhiều environment với config khác nhau. Env var nên được document, validate lúc startup và quản lý qua deployment/config system.

### Nó không phải là gì

Environment Variable không phải nơi an toàn tuyệt đối cho secret. Env var có thể bị lộ qua process dump, logs, shell history, dashboard hoặc crash report nếu xử lý sai. Nó cũng không thay thế config schema; nếu thiếu validation, typo env var có thể làm production chạy sai âm thầm.

## Core Mechanism / Cơ chế lõi

Process đọc env var lúc startup hoặc runtime, parse sang type cần dùng, áp default nếu có, validate required fields, rồi đưa vào config object. Trong container/Kubernetes, env var thường đến từ manifest, ConfigMap, Secret, CI/CD variable hoặc secret manager integration.

## Project Role / Vai trò trong dự án

Environment Variable là node cần mở khi app lỗi chỉ ở production/staging, config drift, missing secret, wrong endpoint, wrong mode hoặc container không đọc được config. Nó giúp team trace config từ source of truth → deploy manifest → runtime process → app config.

## Output / Artifact nên có

- Env var catalog: name, purpose, type, required/default, example, environment scope
- Startup validation: fail fast khi missing/invalid value
- Secret handling note: biến nào nhạy cảm, lấy từ Secret/secret manager nào
- Deployment mapping: local `.env`, Docker Compose, Kubernetes, CI/CD
- Troubleshooting checklist cho missing env, wrong value, stale config và config drift

## Decision Checklist / Câu hỏi kiểm tra

- Env var này là config thường hay secret nhạy cảm?
- Có default an toàn không, hay phải required và fail fast?
- Value có được parse/validate type, range, URL, enum không?
- Tên biến có nhất quán giữa local/staging/production không?
- Có log config summary mà không lộ secret không?
- Khi đổi env var, app có cần restart/redeploy không?
- Source of truth của config nằm ở đâu?

## Failure Modes / Cách nó gây lỗi

- Typo env var làm app dùng default sai và lỗi chỉ lộ ở production.
- Missing required env nhưng app không fail fast, dẫn tới lỗi runtime khó hiểu.
- Secret bị log ra khi in toàn bộ config/env.
- Staging/prod dùng endpoint/API key khác nhưng tên biến giống gây nhầm.
- Container nhận env cũ vì deployment chưa restart/rollout.
- Config drift khi hotfix env trực tiếp ngoài source of truth.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ chạy local có thể dùng config file đơn giản.
- Không nên nhồi config phức tạp dạng JSON lớn vào env var nếu cần schema/versioning rõ.
- Không nên dùng env var làm secret store dài hạn nếu có secret manager/Kubernetes Secret phù hợp hơn.

## Gồm những gì

- [[Secret]]
- [[Deployment]]

## Nối mạnh

- [[Config Drift]] vì env var lệch giữa source of truth và runtime là nguồn drift phổ biến.
- [[Docker Compose]] vì Compose thường inject env var cho service local/staging.
- [[Kubernetes Secret]] vì secret thường được đưa vào Pod qua env var hoặc mounted file.
- [[ConfigMap]] vì config không nhạy cảm trong Kubernetes thường đi qua ConfigMap/env.
- [[Deployment]] vì thay env var thường cần rollout/restart để app nhận config mới.

## Liên quan rộng

- Runtime configuration
- DevOps
- Twelve-Factor App
- Production troubleshooting

## Keywords / Từ khóa tìm kiếm

- Environment Variable
- env var
- biến môi trường
- runtime config
- process environment
- .env file
- config validation
- missing environment variable
- Docker env
- Kubernetes env
- secret env var
- config drift
- environment variable debugging

## Source trace

- Twelve-Factor App config principle
- Deployment and Operations references
