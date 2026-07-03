# Scope

Aliases: project scope, phạm vi

Type: Requirement / Planning

## Context / Ngữ cảnh

Scope xuất hiện khi team cần xác định phần nào sẽ làm, phần nào không làm, và giới hạn nào đang điều khiển quyết định sản phẩm hoặc dự án.

## Boundary / Ranh giới

### Nó là gì

Scope là ranh giới cam kết của work: mục tiêu, feature, requirement, user group, system boundary, constraint và out-of-scope.

### Nó không phải là gì

Nó không phải là wishlist, không phải roadmap mở vô hạn, và không phải danh sách task nếu chưa nói ranh giới deliverable.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là phân tách included, excluded, assumption và dependency. Scope tốt giúp phát hiện scope creep và tạo cơ sở cho change control.

## Project Role / Vai trò trong dự án

Scope giữ cho planning, estimation, design và acceptance cùng nhìn về một ranh giới. Nó giúp team biết khi nào một yêu cầu mới là thay đổi phạm vi chứ không phải chi tiết nhỏ.

## Output / Artifact nên có

- In-scope và out-of-scope rõ ràng
- Assumption, dependency và constraint quan trọng
- Link sang requirement hoặc change control khi có thay đổi

## Decision Checklist / Câu hỏi kiểm tra

- Feature hoặc requirement này có nằm trong cam kết hiện tại không?
- Ai được phục vụ trong scope này, ai không?
- Out-of-scope có được ghi rõ để tránh hiểu nhầm không?
- Thay đổi này có cần change control không?
- Scope có đủ nhỏ để estimate và nghiệm thu không?

## Failure Modes / Cách nó gây lỗi

- Scope creep vì không ghi ranh giới từ đầu
- Team build thêm case không cần thiết vì sợ thiếu
- Stakeholder tưởng một thứ nằm trong scope dù team không tính làm
- Estimate sai vì dependency hoặc out-of-scope không rõ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tài liệu scope nặng cho thử nghiệm cá nhân rất nhỏ
- Dễ over-engineer nếu khóa scope quá sớm khi problem vẫn chưa được hiểu

## Gồm những gì

- [[Requirement]]
- [[Change Control]]

## Nối mạnh

- [[Acceptance Criteria]] vì acceptance criteria cụ thể hóa ranh giới đạt/chưa đạt
- [[Traceability]] vì scope đổi cần truy ra requirement, design và test bị ảnh hưởng

## Liên quan rộng

- Roadmap
- Estimation
- Release planning

## Keywords / Từ khóa tìm kiếm

- Scope
- project scope
- phạm vi
- Requirement
- Change Control
- Scope learning keyword

## Source trace

- Software Requirements 3rd Ed Ch05
