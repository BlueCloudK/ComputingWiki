# Requirements

Aliases: software requirements, requirements engineering, yêu cầu phần mềm

Type: Requirement / Planning

## Context / Ngữ cảnh

Requirements là vùng kiến thức về cách phát hiện, ghi lại, làm rõ, ưu tiên và kiểm soát nhu cầu phần mềm trước khi nó đi vào design, implementation và testing.

## Boundary / Ranh giới

### Nó là gì

Requirements bao phủ requirement statement, stakeholder need, scope, acceptance, traceability và change control. Nó giúp team biết hệ thống cần phục vụ ai, làm gì, dưới ràng buộc nào.

### Nó không phải là gì

Nó không phải là backlog task thuần kỹ thuật, không phải kiến trúc chi tiết, và không phải danh sách mong muốn chưa có owner, scope hoặc tiêu chí kiểm chứng.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đi từ nhu cầu mơ hồ sang artifact có thể quyết định: elicitation, analysis, specification, validation, prioritization và change management. Mỗi artifact phải giảm hiểu nhầm hoặc hỗ trợ quyết định dự án.

## Project Role / Vai trò trong dự án

Requirements là MOC điều hướng cho vùng requirement. Nó giúp đi từ nhu cầu cấp cao xuống node cụ thể như requirement, use case, user story, scope và traceability.

## Output / Artifact nên có

- Requirement set hoặc requirement specification
- Scope boundary, acceptance criteria và stakeholder mapping
- Traceability/change notes cho requirement quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Nhu cầu này đến từ stakeholder hoặc source nào?
- Nó cần biểu diễn bằng requirement, user story hay use case?
- Scope và out-of-scope đã rõ chưa?
- Acceptance criteria và traceability có đủ cho rủi ro hiện tại không?
- Thay đổi requirement có cần change control không?

## Failure Modes / Cách nó gây lỗi

- Nhu cầu bị ghi mơ hồ nên design/test đi lệch
- Scope creep vì không có ranh giới hoặc change control
- Stakeholder quan trọng bị bỏ qua
- Requirement đổi nhưng trace sang test/design không được cập nhật

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần requirements process nặng khi chỉ làm spike để học vấn đề
- Dễ over-engineer nếu yêu cầu nhỏ nào cũng bị ép vào specification dài

## Gồm những gì

- [[Requirement]]
- [[Use Case]]
- [[User Story]]
- [[Scope]]
- [[Traceability]]
- [[Change Control]]

## Nối mạnh

- [[Acceptance Criteria]] vì requirements cần tiêu chí nghiệm thu để tránh mơ hồ
- [[Stakeholder]] vì requirement cần nguồn nhu cầu và người chịu ảnh hưởng rõ

## Liên quan rộng

- Product planning
- Software specification
- Testing strategy
- Release scope

## Source trace

- SWEBOK Map
- Requirements Engineering Map
