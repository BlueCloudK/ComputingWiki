# IDOR

Aliases: Insecure Direct Object Reference, tham chiếu object không an toàn

Type: Security

## Context / Ngữ cảnh

IDOR xuất hiện khi API hoặc app nhận object identifier từ user như `userId`, `orderId`, `fileId`, `projectId`, `tenantId` rồi dùng identifier đó để đọc/ghi resource mà không kiểm tra user có quyền với object đó không. Nó rất hay gặp trong REST API, file download, admin/user profile, invoice/order và multi-tenant SaaS.

## Boundary / Ranh giới

### Nó là gì

IDOR là lỗi object-level authorization: attacker đổi id trong URL/query/body/header để truy cập object không thuộc quyền. Dù id là số tuần tự hay UUID, lỗi chính vẫn là thiếu ownership/permission check ở backend.

### Nó không phải là gì

IDOR không chỉ là “id dễ đoán”. Dùng UUID/opaque id giúp giảm khả năng đoán nhưng không thay thế authorization. IDOR cũng không phải authentication; attacker có thể là user đăng nhập hợp lệ nhưng truy cập resource của user/tenant khác.

## Core Mechanism / Cơ chế lõi

Request chứa object id. Backend load object theo id rồi trả dữ liệu hoặc thực hiện action. Nếu backend không kiểm tra subject hiện tại có quyền với object đó theo owner/tenant/role/relationship/policy, user có thể đổi id và vượt permission boundary.

## Project Role / Vai trò trong dự án

IDOR là node cần mở khi thiết kế endpoint nhận id từ client, file download, object storage URL, admin action hoặc multi-tenant query. Nó giúp team viết test cross-user/cross-tenant và đặt authorization gần data access/use case thay vì tin frontend.

## Output / Artifact nên có

- Object-level authorization rule cho endpoint/resource
- Test case: user A cannot read/update/delete user B resource
- Tenant/owner filter trong query hoặc service layer
- Error behavior: 403 hoặc 404 để tránh leak resource existence nếu cần
- Audit log cho attempt truy cập object không thuộc quyền

## Decision Checklist / Câu hỏi kiểm tra

- Endpoint này nhận object id nào từ client?
- Backend có kiểm tra owner/tenant/permission sau khi biết current user không?
- Query có filter theo tenant/user scope ngay từ đầu không?
- Dùng UUID/opaque id có đi kèm authorization không?
- User có thể đổi id trong URL/body/header để truy cập object khác không?
- Response 403/404 có leak existence nhạy cảm không?
- Có regression test cho cross-user và cross-tenant chưa?

## Failure Modes / Cách nó gây lỗi

- `/users/123` cho user khác xem profile/PII vì chỉ check login.
- `/orders/{id}` update đơn hàng không thuộc user hiện tại.
- File download lấy `fileId` rồi stream file mà không check owner.
- Tenant id trong request body được tin trực tiếp, dẫn tới cross-tenant data leak.
- API dùng UUID nhưng endpoint vẫn trả data nếu attacker có được id từ log/referrer/share link.
- Frontend ẩn object nhưng backend không enforce nên gọi API trực tiếp vẫn được.

## Khi nào chưa cần hoặc dễ over-engineer

- Endpoint public resource thật sự có thể không cần object-level auth, nhưng phải ghi rõ là public.
- Không nên chỉ đổi numeric id sang UUID rồi coi như đã fix IDOR.
- Không nên xây policy engine nặng nếu simple owner/tenant check rõ ràng là đủ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Broken Access Control]] vì IDOR là một dạng access control failure phổ biến.
- [[Authorization]] vì IDOR được chặn bằng object-level authorization.
- [[API Endpoint]] vì endpoint nhận object id là nơi IDOR thường xuất hiện.
- [[Service Layer]] vì use case service thường là nơi enforce owner/tenant rule.
- [[Logging]] vì attempt truy cập object trái quyền cần audit/debug.

## Liên quan rộng

- Application security
- API security
- Multi-tenant design
- Object ownership

## Keywords / Từ khóa tìm kiếm

- IDOR
- Insecure Direct Object Reference
- tham chiếu object không an toàn
- object level authorization
- ownership check
- tenant filter
- user id enumeration
- cross tenant access
- authorization bypass
- broken object level authorization
- BOLA
- IDOR testing
- IDOR debugging

## Source trace

- OWASP API Security Top 10
- OWASP Access Control Cheat Sheet
