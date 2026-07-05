# Least Privilege

Aliases: principle of least privilege, quyền tối thiểu, minimum permission

Type: Security

## Context / Ngữ cảnh

Least Privilege xuất hiện khi user, service account, API key, database user, container, CI job hoặc cloud role chỉ nên có quyền đúng với nhiệm vụ cần làm. Nó là nguyên tắc giảm blast radius khi credential bị lộ, bug bị khai thác hoặc thao tác nhầm xảy ra.

## Boundary / Ranh giới

### Nó là gì

Least Privilege là nguyên tắc cấp quyền tối thiểu hợp lý theo principal, action, resource, scope và lifetime. Quyền nên đủ để hệ thống vận hành nhưng không rộng hơn nhu cầu thật. Nó thường đi cùng RBAC/ABAC/IAM policy, scoped token, read-only role, temporary access và periodic access review.

### Nó không phải là gì

Least Privilege không phải deny mọi thứ tới mức hệ thống không vận hành được. Nó cũng không thay thế monitoring, audit, approval hoặc incident response. Quyền tối thiểu phải dựa trên use case thật và được kiểm chứng, không phải cắt quyền mù làm team phải bypass bằng admin key.

## Core Mechanism / Cơ chế lõi

Team liệt kê principal cần quyền, action cần thực hiện, resource được phép tác động, condition/scope áp dụng và thời hạn quyền. Policy được review để bỏ wildcard, bỏ quyền admin mặc định, tách read/write/delete, dùng temporary credential nếu có thể, rồi audit usage để loại quyền không dùng.

## Project Role / Vai trò trong dự án

Least Privilege là node cần mở khi tạo API key, service account, Kubernetes RBAC, cloud IAM role, database user, CI/CD token hoặc agent/tool permission. Nó giúp team hỏi: nếu token này lộ, attacker làm được gì và có cách giảm impact không.

## Output / Artifact nên có

- Permission matrix: principal → action → resource → scope/condition
- Role/policy review note: wildcard, admin, cross-tenant, delete/write permission
- Temporary access rule: expiry, approval, break-glass account nếu cần
- Secret/token scope và rotation plan
- Audit signal: permission used, denied action, unusual access, unused permission

## Decision Checklist / Câu hỏi kiểm tra

- Principal này thật sự cần action nào để hoàn thành nhiệm vụ?
- Resource scope có bị `*`, all tenant, all bucket hoặc all database quá rộng không?
- Có tách read/write/delete/admin không?
- Credential có lifetime/expiry/rotation không?
- Có quyền nào không dùng nhưng vẫn còn trong policy không?
- Nếu principal bị compromise, blast radius là gì?
- Có log/audit để biết quyền này được dùng khi nào không?

## Failure Modes / Cách nó gây lỗi

- Service thường dùng admin role vì cấu hình nhanh.
- API key production dùng chung nhiều service nên lộ một nơi ảnh hưởng toàn hệ thống.
- Database user của app có quyền DROP/ALTER trong runtime bình thường.
- CI token có quyền write/delete secret hoặc deploy mọi environment không cần thiết.
- Kubernetes ServiceAccount có quyền list/read Secret toàn namespace/cluster.
- Quyền quá vụn nhưng thiếu workflow cấp tạm thời khiến team chia sẻ admin credential ngoài luồng.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype local không dữ liệu nhạy có thể dùng role đơn giản, nhưng cần tách khỏi production.
- Không nên chia quyền quá nhỏ nếu không có tooling/owner để vận hành.
- Không nên dùng least privilege như lý do chặn mọi việc; mục tiêu là giảm risk có kiểm soát.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authorization]] vì least privilege là nguyên tắc thiết kế quyền.
- [[IAM]] vì cloud IAM cần scope permission theo principal/action/resource.
- [[Kubernetes RBAC]] vì ServiceAccount/Role/RoleBinding cần quyền tối thiểu.
- [[Secret]] vì secret/token nên có scope nhỏ và vòng đời rõ.
- [[Broken Access Control]] vì quyền quá rộng làm access control failure có blast radius lớn hơn.

## Liên quan rộng

- Access control
- Blast radius
- Security operations
- Credential management

## Keywords / Từ khóa tìm kiếm

- Least Privilege
- principle of least privilege
- quyền tối thiểu
- minimum permission
- permission scope
- scoped token
- IAM least privilege
- RBAC least privilege
- wildcard permission
- admin role risk
- blast radius
- access review
- temporary access
- least privilege debugging

## Source trace

- OWASP Authorization Cheat Sheet
- AWS Well-Architected Security Pillar
