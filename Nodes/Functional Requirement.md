# Functional Requirement

Aliases: function requirement, yêu cầu chức năng

Type: Requirement / Planning

## Context / Ngữ cảnh

Functional Requirement xuất hiện khi cần mô tả hệ thống phải làm hành vi gì cho user, actor hoặc hệ thống bên ngoài. Nó trả lời câu hỏi "hệ thống phải thực hiện chức năng nào".

## Boundary / Ranh giới

### Nó là gì

Functional Requirement là yêu cầu về hành vi quan sát được: input, action, business rule, state change, output hoặc response của hệ thống.

### Nó không phải là gì

Nó không phải là quality target như latency hay availability, không phải thiết kế UI chi tiết, và không phải implementation task nếu chưa nói hành vi cần đạt.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là mô tả actor, trigger, điều kiện trước, hành vi hệ thống, kết quả và exception path. Một functional requirement tốt có thể chuyển thành use case, API behavior hoặc acceptance criteria.

## Project Role / Vai trò trong dự án

Functional Requirement định hình backlog, API contract, domain logic và test case chức năng. Nó là phần dễ thấy nhất của phạm vi sản phẩm.

## Output / Artifact nên có

- Mô tả hành vi hệ thống cần thực hiện
- Business rule, input/output và state change quan trọng
- Acceptance criteria hoặc use case liên quan

## Decision Checklist / Câu hỏi kiểm tra

- Actor hoặc hệ thống gọi chức năng này là ai?
- Trigger nào làm hành vi bắt đầu?
- Output hoặc state cuối mong đợi là gì?
- Có business rule hoặc exception path nào bắt buộc không?
- Requirement này có thể test bằng một scenario cụ thể không?

## Failure Modes / Cách nó gây lỗi

- Viết thành task kỹ thuật nên mất mục tiêu người dùng
- Chỉ ghi happy path, bỏ sót lỗi, permission hoặc dữ liệu biên
- Trộn lẫn quality target khiến scope bị nhập nhằng
- Không có acceptance criteria nên dev/test hiểu khác nhau

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần formal hóa dài khi team đang sketch ý tưởng ở mức rất thô
- Dễ over-engineer nếu biến từng thao tác UI nhỏ thành requirement riêng không có giá trị trace

## Gồm những gì

- [[Use Case]]
- [[Acceptance Criteria]]

## Nối mạnh

- [[Requirement]] vì functional requirement là một loại requirement chính
- [[Nonfunctional Requirement]] vì cùng một chức năng thường có ràng buộc chất lượng đi kèm

## Liên quan rộng

- Product backlog
- Domain logic
- API behavior

## Keywords / Từ khóa tìm kiếm

- Functional Requirement
- function requirement
- yêu cầu chức năng
- functional
- requirement
- Planning
- yêu cầu

## Source trace

- Requirements Engineering Map / Software Requirements 3rd Ed Ch01
