# Config Drift

Aliases: configuration drift, drift cấu hình

Type: Failure Pattern / Operations

## Context / Ngữ cảnh

Config Drift xuất hiện khi cấu hình runtime của môi trường thật khác với source of truth như Git, IaC, Helm values, Terraform state, Ansible playbook hoặc tài liệu vận hành. Nó thường làm dev/staging/prod có behavior khác nhau dù code giống nhau.

## Boundary / Ranh giới

### Nó là gì

Config Drift là failure pattern trong đó cấu hình đang chạy lệch khỏi cấu hình mong muốn hoặc cấu hình đã được review. Drift có thể nằm ở environment variable, feature flag, secret, firewall rule, Kubernetes manifest, database setting, cloud resource hoặc config file sửa tay trên server.

### Nó không phải là gì

Config Drift không phải mọi khác biệt cấu hình. Một số khác biệt giữa dev/staging/prod là chủ ý. Drift là khác biệt không được quản lý, không được review hoặc không còn khớp source of truth. Nó cũng không chỉ là lỗi DevOps; app behavior và security có thể lệch vì drift.

## Core Mechanism / Cơ chế lõi

Drift thường sinh ra từ hotfix thủ công, thay đổi qua console, script một lần, secret/config update ngoài Git, apply thiếu bước hoặc rollback không đồng bộ. Khi source of truth không được reconcile với runtime, hệ thống dần mất khả năng tái tạo môi trường và debug vì “config thật” không còn giống thứ team nghĩ.

## Project Role / Vai trò trong dự án

Config Drift là node cần mở khi chỉ production lỗi, một node chạy khác node khác, redeploy không tái tạo được behavior, hoặc IaC plan phát hiện resource đã bị sửa ngoài luồng. Nó giúp team kiểm tra source of truth, runtime diff, change history và cơ chế reconciliation.

## Output / Artifact nên có

- Source of truth rõ: Git/IaC/Helm/Config service nào sở hữu config nào
- Drift detection report: runtime config vs declared config
- Change audit: ai đổi, đổi khi nào, qua pipeline hay manual
- Reconciliation plan: revert runtime hay cập nhật source of truth
- Policy hạn chế manual change ở production và yêu cầu PR/change record

## Decision Checklist / Câu hỏi kiểm tra

- Config runtime hiện tại có khớp Git/IaC/Helm values không?
- Khác biệt giữa environment là intentional hay drift?
- Ai có quyền sửa config trực tiếp ngoài pipeline?
- Có log/audit trail cho thay đổi config không?
- Drift được detect tự động hay chỉ biết khi incident xảy ra?
- Rollback/deploy có khôi phục config về source of truth không?
- Secret/feature flag có source of truth và history riêng không?

## Failure Modes / Cách nó gây lỗi

- Production có env var khác staging làm bug không reproduce được.
- Config sửa tay trên server mất sau redeploy/restart và làm hệ thống đổi behavior bất ngờ.
- Firewall/cloud setting chỉnh ngoài Terraform làm IaC apply sau đó phá route hoặc expose sai.
- Helm values runtime lệch chart Git làm rollback/upgrade khó đoán.
- Feature flag bật/tắt ngoài quy trình làm user thấy behavior khác nhau không có trace.
- Secret/config drift làm một instance gọi endpoint khác instance còn lại.

## Khi nào chưa cần hoặc dễ over-engineer

- Project cá nhân nhỏ có thể chấp nhận config thủ công nếu ghi chú rõ và ít môi trường.
- Không nên triển khai governance nặng nếu chưa có nhiều người/môi trường/resource.
- Không nên coi mọi khác biệt là drift; khác biệt intentional cần được document và version.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Infrastructure as Code]] vì IaC thường là source of truth để phát hiện drift.
- [[GitOps]] vì GitOps dựa trên reconciliation giữa Git và runtime state.
- [[ConfigMap]] vì config Kubernetes có thể drift giữa manifest và cluster.
- [[Deployment]] vì deploy/rollback phải kiểm soát config đi kèm code.

## Liên quan rộng

- Operations reliability
- Environment parity
- Change management
- Incident debugging

## Keywords / Từ khóa tìm kiếm

- Config Drift
- configuration drift
- drift cấu hình
- runtime config mismatch
- environment drift
- IaC drift
- Terraform drift
- GitOps drift
- config source of truth
- manual change
- config reconciliation
- production config mismatch
- Helm values drift
- drift detection

## Source trace

- Terraform drift documentation
- GitOps references
