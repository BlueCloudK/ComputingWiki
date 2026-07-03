# Change Control

Aliases: change management, kiểm soát thay đổi

Type: Requirement / Planning

## Context / Ngữ cảnh

Change Control xuất hiện khi requirement, scope hoặc system behavior đã được thống nhất nhưng có yêu cầu thay đổi cần đánh giá tác động trước khi nhận vào.

## Boundary / Ranh giới

### Nó là gì

Change Control là cơ chế ghi nhận, đánh giá, approve/reject và trace một thay đổi đối với scope, requirement, design hoặc release.

### Nó không phải là gì

Nó không phải là cấm thay đổi, không phải bureaucracy cho mọi chỉnh sửa nhỏ, và không thay thế trao đổi trực tiếp khi team còn đang khám phá.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là biến change request thành quyết định có context: lý do đổi, artifact bị ảnh hưởng, effort, risk, priority, owner và trạng thái approve.

## Project Role / Vai trò trong dự án

Change Control giúp team không âm thầm đổi scope rồi làm lệch timeline, test plan hoặc expectation. Nó đặc biệt hữu ích khi nhiều stakeholder cùng tác động vào sản phẩm.

## Output / Artifact nên có

- Change request hoặc decision note
- Impact analysis lên requirement, scope, design, test và release
- Quyết định approve/reject/defer cùng lý do

## Decision Checklist / Câu hỏi kiểm tra

- Thay đổi này giải quyết vấn đề gì?
- Nó ảnh hưởng requirement, scope, test hoặc release nào?
- Ai có quyền approve thay đổi này?
- Cost/risk của thay đổi có xứng với value không?
- Nếu defer, có cần ghi lại assumption hoặc follow-up không?

## Failure Modes / Cách nó gây lỗi

- Scope creep vì thay đổi nhỏ tích tụ thành cam kết mới
- Test/design không cập nhật theo requirement mới
- Stakeholder tưởng thay đổi đã được nhận dù team chưa approve
- Quy trình quá nặng làm team né ghi nhận thay đổi

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần board phê duyệt nặng cho project cá nhân hoặc discovery sớm
- Dễ over-engineer nếu mọi typo hoặc microcopy đều cần change request

## Gồm những gì

- [[Scope]]
- [[Traceability]]

## Nối mạnh

- [[Requirement]] vì change control thường bắt đầu từ thay đổi requirement
- [[Acceptance Criteria]] vì criteria cần đổi khi điều kiện nghiệm thu đổi

## Liên quan rộng

- Release governance
- Stakeholder approval
- Impact analysis

## Keywords / Từ khóa tìm kiếm

- Change Control
- change management
- kiểm soát thay đổi
- Scope
- Traceability
- Change Control learning keyword

## Source trace

- Software Requirements 3rd Ed Ch28
