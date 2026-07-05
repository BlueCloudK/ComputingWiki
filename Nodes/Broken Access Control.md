# Broken Access Control

Aliases: Broken Access Control, broken access control, access control failure, lỗi phân quyền

Type: Security Attack Pattern

## Context / Ngữ cảnh

Broken Access Control xuất hiện khi user/service có thể truy cập resource hoặc thực hiện action ngoài quyền được cấp. Đây là nhóm lỗi bảo mật rất phổ biến ở API, admin panel, multi-tenant app, file download, object storage, workflow approval và service-to-service call.

## Boundary / Ranh giới

### Nó là gì

Broken Access Control là failure mode khi authorization rule bị thiếu, đặt sai layer, kiểm tra sai resource/action/context hoặc chỉ enforce ở frontend. Nó thường dẫn tới IDOR, privilege escalation, tenant data leak, bypass approval hoặc user thao tác trên object không thuộc quyền.

### Nó không phải là gì

Broken Access Control không phải lỗi authentication đơn thuần. User có thể đăng nhập hợp lệ nhưng vẫn không được phép xem/sửa resource cụ thể. Nó cũng không phải chỉ là “ẩn nút trên UI”; attacker có thể gọi API trực tiếp nếu backend không enforce quyền.

## Core Mechanism / Cơ chế lõi

Request đi vào với subject đã xác thực. Hệ thống phải kiểm tra subject-action-resource-context trước khi trả dữ liệu hoặc thực hiện side effect. Lỗi xảy ra khi code chỉ check role chung, bỏ owner/tenant filter, tin client-provided id, thiếu policy ở endpoint mới hoặc query trả dữ liệu trước khi filter quyền.

## Project Role / Vai trò trong dự án

Broken Access Control là node cần mở khi review endpoint, file API, admin action, multi-tenant query hoặc workflow approval. Nó giúp team tạo test “user A không xem/sửa được resource của user B”, kiểm tra backend enforcement và audit log cho hành động nhạy cảm.

## Output / Artifact nên có

- Permission matrix: subject/role → action → resource/scope
- Object-level authorization test cho từng endpoint nhạy cảm
- Tenant/owner filter rule ở query/data access layer
- Security regression test cho IDOR, privilege escalation, forbidden action
- Audit log: subject, action, resource, decision, reason cho action nhạy cảm

## Decision Checklist / Câu hỏi kiểm tra

- Endpoint/action này bảo vệ resource nào?
- Ai được làm action này và trong context nào?
- Backend có enforce quyền trước khi đọc/ghi dữ liệu không?
- Query có filter tenant/owner/resource scope không?
- User có thể đổi id/path/body để truy cập object khác không?
- Role check có đủ không, hay cần ownership/relationship/policy check?
- Có test forbidden/cross-tenant/cross-user cho endpoint này không?

## Failure Modes / Cách nó gây lỗi

- UI ẩn nút nhưng API vẫn cho gọi action nhạy cảm.
- User đổi `userId`, `orderId`, `projectId` trong URL/body để xem/sửa dữ liệu người khác.
- Query thiếu tenant filter làm lộ data giữa tổ chức.
- Admin endpoint chỉ check login mà không check role/permission.
- Cache permission stale làm quyền đã thu hồi vẫn dùng được.
- Service nội bộ tin header/client claim không được verify.

## Khi nào chưa cần hoặc dễ over-engineer

- Feature prototype một user, không dữ liệu nhạy có thể bắt đầu permission nhẹ, nhưng cần đánh dấu rõ trước khi mở nhiều user.
- Không nên xây policy engine phức tạp nếu permission matrix đơn giản đủ dùng.
- Không nên chỉ dùng role-level check nếu resource ownership mới là rule thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Authorization]] vì Broken Access Control là failure mode trực tiếp của authorization.
- [[IDOR]] vì IDOR là dạng phổ biến của object-level access control failure.
- [[Authentication]] vì cần identity đáng tin trước khi kiểm tra quyền.
- [[Stale Cache]] vì cache quyền cũ có thể giữ access đã bị thu hồi.
- [[API Endpoint]] vì mỗi endpoint cần access control rule rõ.

## Liên quan rộng

- Application security
- Threat modeling
- Security testing
- Multi-tenant design

## Keywords / Từ khóa tìm kiếm

- Broken Access Control
- broken access control
- access control failure
- lỗi phân quyền
- authorization bypass
- privilege escalation
- IDOR
- tenant isolation
- object level authorization
- ownership check
- permission bypass
- backend authorization
- access control testing
- broken access control debugging

## Source trace

- OWASP Top 10
- OWASP API Security Top 10
- OWASP Access Control Cheat Sheet
