# Stakeholder

Aliases: interested party, bên liên quan

Type: Requirement / Planning

## Context / Ngữ cảnh

Stakeholder xuất hiện khi requirement hoặc decision cần biết ai có nhu cầu, ai bị ảnh hưởng, ai có quyền quyết định và ai có thể cung cấp thông tin đúng.

## Boundary / Ranh giới

### Nó là gì

Stakeholder là người, nhóm hoặc tổ chức có lợi ích, trách nhiệm, rủi ro hoặc quyền quyết định liên quan tới hệ thống.

### Nó không phải là gì

Nó không chỉ là end user, không phải tên phòng ban cho có, và không thay thế việc hiểu mục tiêu, pain point hoặc quyền hạn của từng nhóm.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là xác định vai trò của stakeholder: user, buyer, operator, regulator, maintainer, support, security, business owner hoặc system consumer. Mỗi vai trò có nhu cầu và tiêu chí chấp nhận khác nhau.

## Project Role / Vai trò trong dự án

Stakeholder giúp requirement có nguồn rõ ràng và giúp team xử lý conflict. Khi hai yêu cầu mâu thuẫn, biết stakeholder nào chịu ảnh hưởng giúp ra quyết định thực tế hơn.

## Output / Artifact nên có

- Danh sách stakeholder và vai trò
- Nhu cầu, pain point, quyền quyết định và mức ảnh hưởng
- Mapping từ stakeholder sang requirement hoặc use case

## Decision Checklist / Câu hỏi kiểm tra

- Ai trực tiếp dùng hệ thống?
- Ai vận hành, bảo trì, hỗ trợ hoặc chịu rủi ro?
- Ai có quyền approve hoặc reject requirement?
- Stakeholder nào đang bị đại diện thiếu?
- Conflict giữa stakeholder được xử lý bằng tiêu chí nào?

## Failure Modes / Cách nó gây lỗi

- Chỉ nghe buyer mà bỏ qua operator hoặc support
- Requirement bị lệch vì stakeholder thật không được phỏng vấn
- Quyết định chậm vì không rõ ai có quyền chốt
- Một nhóm chịu rủi ro security/compliance nhưng không có tiếng nói

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần stakeholder map phức tạp cho tool cá nhân hoặc prototype nhỏ
- Dễ over-engineer nếu liệt kê mọi người liên quan nhưng không gắn với quyết định nào

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Requirement]] vì stakeholder là nguồn hoặc người chịu ảnh hưởng của requirement
- [[Use Case]] vì use case cần actor và goal rõ
- [[Scope]] vì stakeholder giúp xác định ai nằm trong phạm vi phục vụ

## Liên quan rộng

- User research
- Governance
- Product ownership

## Keywords / Từ khóa tìm kiếm

- Stakeholder
- interested party
- bên liên quan
- Stakeholder learning keyword
- Stakeholder debug keyword
- Stakeholder design keyword

## Source trace

- Requirements Engineering - A Good Practice Guide Ch04.3
