# Secret

Aliases: API key, token, password, bí mật

Type: Security / Operations

## Context / Ngữ cảnh

Secret xuất hiện khi hệ thống cần dùng thông tin nhạy cảm để xác thực, ký request, truy cập database, gọi third-party API, giải mã dữ liệu hoặc vận hành infrastructure. Ví dụ gồm password, API key, access token, private key, certificate key, database credential và webhook signing secret.

## Boundary / Ranh giới

### Nó là gì

Secret là dữ liệu nếu lộ ra thì attacker có thể giả danh, truy cập tài nguyên, đọc/ghi dữ liệu hoặc phá hệ thống. Secret cần được tạo, lưu, truyền, dùng, rotate và revoke theo lifecycle rõ. Nó phải được phân biệt với config thường như port, feature flag hoặc public endpoint.

### Nó không phải là gì

Secret không phải mọi environment variable. Không phải mọi config đều nhạy cảm. Ngược lại, secret không trở nên an toàn chỉ vì được base64 encode, giấu trong `.env`, đặt trong CI variable hoặc Kubernetes Secret. Secret cũng không nên hard-code trong source code, log, image, tài liệu hoặc test fixture public.

## Core Mechanism / Cơ chế lõi

Secret được tạo với entropy đủ mạnh, lưu trong secret manager/vault/Kubernetes Secret/CI secret store, cấp cho workload theo least privilege, dùng qua env var hoặc mounted file, được mask khỏi log, và rotate/revoke khi hết hạn, nghi ngờ lộ hoặc đổi quyền. Audit log giúp biết ai/what đã đọc hoặc dùng secret.

## Project Role / Vai trò trong dự án

Secret là node cần mở khi deploy app, cấu hình integration, review security, debug 401/403 từ provider hoặc xử lý incident lộ credential. Nó giúp team trace secret từ source of truth tới runtime và tránh nhầm giữa config thường, credential nhạy cảm và public token.

## Output / Artifact nên có

- Secret inventory: name, owner, purpose, scope, environment, rotation interval
- Storage/delivery decision: secret manager, Kubernetes Secret, CI secret, env var, mounted file
- Access policy: ai/service nào được đọc, quyền tối thiểu nào cần có
- Rotation/revoke runbook và validation sau rotation
- Leak prevention checklist: no commit, no log, no screenshot, no public artifact

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu này nếu lộ thì attacker làm được gì?
- Secret được lưu ở đâu và ai có quyền đọc?
- Workload nhận secret qua env var, mounted file hay SDK secret manager?
- Secret có bị log, crash dump, shell history hoặc CI output lộ không?
- Có rotation/revoke path không?
- Scope secret có quá rộng không, ví dụ key production dùng cho mọi service?
- Có detect secret leak trong Git/CI/log không?

## Failure Modes / Cách nó gây lỗi

- Secret hard-code trong repo hoặc commit nhầm vào history.
- Log toàn bộ config/env làm token/password xuất hiện trong log aggregator.
- Một API key dùng chung quá rộng, lộ một nơi làm nhiều service bị compromise.
- Không rotate/revoke khi developer rời team hoặc key nghi ngờ bị lộ.
- Secret nằm trong image/container layer nên ai pull image cũng đọc được.
- Secret expired/rotated nhưng workload chưa reload, gây outage 401/403.

## Khi nào chưa cần hoặc dễ over-engineer

- Public identifier, public API endpoint hoặc client id public không nên bị quản lý như secret nếu không nhạy cảm.
- Local prototype có thể dùng `.env`, nhưng không nên commit và cần tách khỏi production secret.
- Không nên tự xây secret manager nếu cloud/Kubernetes/CI đã có cơ chế phù hợp và audit tốt.

## Gồm những gì

- [[Environment Variable]]

## Nối mạnh

- [[Kubernetes Secret]] vì Kubernetes Secret là cách cấp secret cho workload trong cluster.
- [[Environment Variable]] vì nhiều app nhận secret qua env var nhưng cần tránh log/lộ.
- [[Authentication]] vì secret thường dùng để chứng minh identity của user/service/client.
- [[Authorization]] vì scope/quyền của secret quyết định impact khi bị lộ.
- [[Least Privilege]] vì secret nên có quyền tối thiểu và phạm vi nhỏ nhất.

## Liên quan rộng

- Secrets management
- Credential rotation
- CI/CD security
- Incident response

## Keywords / Từ khóa tìm kiếm

- Secret
- bí mật
- API key
- token
- password
- credential
- private key
- webhook secret
- secret manager
- secret rotation
- secret leak
- hardcoded secret
- env secret
- credential scope
- secret management debugging

## Source trace

- OWASP Secrets Management Cheat Sheet
