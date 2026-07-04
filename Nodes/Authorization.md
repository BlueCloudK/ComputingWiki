# Authorization

Aliases: access control, permission, phân quyền, authz, access permission, phân quyền truy cập

Type: Security

## Context / Ngữ cảnh

Authorization xuất hiện sau khi hệ thống đã biết actor là ai và cần quyết định actor đó có được truy cập resource hoặc thực hiện action cụ thể không. Nó nằm ở mọi boundary có dữ liệu hoặc hành động nhạy cảm: API, database query, admin UI, file download, tool call, tenant/project boundary và service-to-service call.

## Boundary / Ranh giới

### Nó là gì

Authorization là kiểm tra quyền: subject nào được làm action nào trên resource nào trong context nào. Nó có thể dựa trên role, permission, policy, ownership, tenant, organization, relationship hoặc attribute. Authorization tốt phải được enforce ở backend/trusted layer, không chỉ ở UI.

### Nó không phải là gì

Authorization không phải Authentication. Login thành công chỉ chứng minh actor là ai, không chứng minh actor được xem/sửa mọi resource. Authorization cũng không phải chỉ ẩn nút trên frontend; nếu backend không kiểm tra, attacker vẫn có thể gọi API trực tiếp.

## Core Mechanism / Cơ chế lõi

Request đi vào hệ thống với subject đã xác thực. Authorization lấy subject, action, resource và context rồi kiểm tra policy/permission trước khi cho handler/service/data access chạy. Với dữ liệu nhiều tenant/user, permission phải đi cùng query/data filter để tránh IDOR hoặc cross-tenant leakage.

## Project Role / Vai trò trong dự án

Authorization ảnh hưởng trực tiếp tới bảo mật dữ liệu, multi-tenant boundary, admin function, API design và audit. Khi review endpoint, team phải hỏi: ai được gọi action này, quyền được enforce ở đâu, resource ownership kiểm tra thế nào, và test có chứng minh user A không xem/sửa được resource của user B không.

## Output / Artifact nên có

- Permission matrix: role/subject → action → resource scope
- Policy decision point/enforcement point note: middleware, service, query layer, gateway
- Ownership/tenant filter rule cho database/file/object access
- Test case: allowed, forbidden, cross-user, cross-tenant, disabled role, privilege escalation
- Audit log cho hành động nhạy cảm: subject, action, resource, decision, reason

## Decision Checklist / Câu hỏi kiểm tra

- Subject là ai và lấy identity từ đâu?
- Resource/action cụ thể cần bảo vệ là gì?
- Rule dựa trên role, ownership, tenant, relationship hay attribute?
- Authorization được enforce ở backend/service/query layer hay chỉ UI?
- Query có filter tenant/owner trước khi trả dữ liệu không?
- Forbidden trả 403, unauthenticated trả 401, not found có cần che existence không?
- Có test IDOR/cross-tenant/cross-user cho endpoint này không?

## Failure Modes / Cách nó gây lỗi

- Backend thiếu authorization vì frontend đã ẩn nút nhưng API vẫn gọi được.
- IDOR: user đổi id trong URL để xem/sửa resource người khác.
- Tenant filter thiếu trong query làm lộ dữ liệu tổ chức khác.
- Role quá rộng hoặc permission wildcard làm user có quyền ngoài nhu cầu.
- Cache permission stale khiến quyền đã thu hồi vẫn còn hiệu lực.
- Policy nằm rải rác nhiều nơi làm endpoint mới dễ quên check quyền.
- Error response tiết lộ resource tồn tại dù user không có quyền biết.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype cá nhân một user có thể dùng authorization rất nhẹ, nhưng phải đánh dấu rõ trước khi mở nhiều user.
- Không nên xây policy engine phức tạp nếu permission matrix đơn giản đủ dùng.
- Không nên chỉ dùng role nếu rule thật phụ thuộc ownership/tenant/resource relation.

## Gồm những gì

- [[Authentication]]
- [[Secret]]

## Nối mạnh

- [[Authentication]] vì authorization cần identity đã xác thực để ra quyết định quyền.
- [[Access Control]] vì authorization là phần lõi của access control.
- [[Kubernetes RBAC]] vì RBAC là một dạng authorization trong Kubernetes.
- [[API Endpoint]] vì mỗi endpoint cần rule quyền rõ.
- [[Stale Cache]] vì cache quyền cũ có thể gây lỗi phân quyền.

## Liên quan rộng

- Application security
- Multi-tenant design
- Audit logging
- Policy enforcement

## Keywords / Từ khóa tìm kiếm

- Authorization
- authz
- access control
- permission
- phân quyền
- phân quyền truy cập
- permission check
- role based access
- RBAC
- ABAC
- policy enforcement
- IDOR
- tenant isolation
- ownership check
- authorization debugging

## Source trace

- OWASP Access Control Cheat Sheet
- OWASP API Security Top 10
