# Kubernetes RBAC

Aliases: RBAC Kubernetes, role based access control

Type: Kubernetes / Security

## Context / Ngữ cảnh

Kubernetes RBAC xuất hiện khi cluster cần phân quyền user, group hoặc service account được làm gì với Kubernetes resources. Nó đặc biệt quan trọng cho CI/CD, controller/operator, app workload, platform team và multi-tenant cluster.

## Boundary / Ranh giới

### Nó là gì

Kubernetes RBAC là cơ chế authorization dựa trên Role, ClusterRole, RoleBinding và ClusterRoleBinding. Nó gán quyền theo verb như get/list/watch/create/update/delete lên resource trong namespace hoặc toàn cluster cho subject như User, Group hoặc ServiceAccount.

### Nó không phải là gì

Kubernetes RBAC không phải authentication. Nó không xác minh danh tính ban đầu; nó chỉ quyết định subject đã được xác thực có được phép làm hành động cụ thể không. RBAC cũng không thay thế network policy, pod security, secret management hoặc application-level authorization.

## Core Mechanism / Cơ chế lõi

Role/ClusterRole định nghĩa quyền, RoleBinding/ClusterRoleBinding gắn quyền đó vào subject. Role giới hạn trong namespace, ClusterRole có thể dùng toàn cluster hoặc bind vào namespace. ServiceAccount của Pod quyết định workload trong cluster có quyền gọi Kubernetes API tới mức nào.

## Project Role / Vai trò trong dự án

Kubernetes RBAC ảnh hưởng trực tiếp tới bảo mật cluster và khả năng app/controller hoạt động. Khi debug Kubernetes, lỗi thiếu quyền thường xuất hiện như forbidden khi controller, CI job hoặc Pod gọi API. Khi review security, cần tìm service account quá quyền như cluster-admin hoặc quyền ghi secret/pod/exec không cần thiết.

## Output / Artifact nên có

- RBAC manifest: Role/ClusterRole và RoleBinding/ClusterRoleBinding
- ServiceAccount permission matrix cho app, CI/CD và controller
- Least-privilege review note: resource, verb, namespace scope
- Test bằng `kubectl auth can-i` cho subject quan trọng
- Runbook cho lỗi forbidden và over-permissioned service account

## Decision Checklist / Câu hỏi kiểm tra

- Subject là user, group hay service account nào?
- Quyền cần namespace-scoped Role hay cluster-scoped ClusterRole?
- Verb có quá rộng không, ví dụ `*` hoặc delete/update không cần thiết?
- Resource có nhạy cảm không, như secrets, pods/exec, roles, rolebindings?
- Pod đang dùng service account mặc định hay service account riêng?
- Có thể kiểm tra bằng `kubectl auth can-i` không?
- CI/CD hoặc controller có đang giữ quyền cluster-admin quá lâu không?

## Failure Modes / Cách nó gây lỗi

- RBAC thiếu quyền làm controller/operator không reconcile được và log forbidden.
- ServiceAccount mặc định bị dùng cho nhiều Pod làm khó kiểm soát quyền.
- ClusterRoleBinding quá rộng cấp quyền toàn cluster cho workload chỉ cần một namespace.
- Quyền secrets/pods/exec quá rộng làm tăng rủi ro privilege escalation.
- RoleBinding trỏ sai namespace hoặc subject làm quyền tưởng đã cấp nhưng không có hiệu lực.
- Debug bằng cách cấp cluster-admin tạm thời rồi quên thu hồi.

## Khi nào chưa cần hoặc dễ over-engineer

- Cluster dev cá nhân có thể bắt đầu đơn giản, nhưng production vẫn cần service account riêng cho workload quan trọng.
- Không nên tạo nhiều Role quá vụn nếu team không quản lý nổi ownership và review.
- Không nên dùng RBAC để giải quyết authorization bên trong application; đó là tầng app/domain riêng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kubernetes]] vì RBAC là authorization layer của Kubernetes API.
- [[Kubernetes Controller]] vì controller cần RBAC đúng để watch và update resources.
- [[Service Account]] vì workload thường nhận quyền Kubernetes qua service account.
- [[Least Privilege]] vì RBAC production nên thiết kế theo quyền tối thiểu.

## Liên quan rộng

- Cluster security
- CI/CD permission
- Multi-tenant Kubernetes
- Platform governance

## Keywords / Từ khóa tìm kiếm

- Kubernetes RBAC
- RBAC Kubernetes
- role based access control
- Role
- ClusterRole
- RoleBinding
- ClusterRoleBinding
- ServiceAccount
- least privilege
- kubectl auth can-i
- forbidden error
- cluster-admin
- Kubernetes authorization
- service account permission

## Source trace

- Kubernetes RBAC documentation
