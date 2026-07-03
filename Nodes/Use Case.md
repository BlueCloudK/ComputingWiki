# Use Case

Aliases: usage scenario, ca sử dụng

Type: Requirement / Planning

## Context / Ngữ cảnh

Use Case xuất hiện khi cần mô tả cách một actor đạt mục tiêu thông qua tương tác với hệ thống. Nó hữu ích khi hành vi có nhiều bước, nhiều nhánh hoặc nhiều actor.

## Boundary / Ranh giới

### Nó là gì

Use Case là mô tả goal-driven về actor, trigger, main flow, alternative flow, exception flow và kết quả mong muốn.

### Nó không phải là gì

Nó không phải là thiết kế màn hình, không phải sequence diagram bắt buộc, và không phải user story ngắn nếu chưa mô tả flow tương tác.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đi từ mục tiêu của actor sang chuỗi tương tác có điều kiện: precondition, main success scenario, variation, error handling và postcondition.

## Project Role / Vai trò trong dự án

Use Case giúp team nhìn hành vi theo luồng nghiệp vụ thay vì chỉ theo task rời rạc. Nó tạo nền cho requirement, test scenario và API/UX boundary.

## Output / Artifact nên có

- Actor và goal
- Main flow, alternative flow và exception flow
- Preconditions, postconditions và acceptance criteria liên quan

## Decision Checklist / Câu hỏi kiểm tra

- Actor chính là ai và họ muốn đạt goal gì?
- Trigger bắt đầu flow là gì?
- Main success path có kết quả rõ không?
- Alternative/error path nào thay đổi requirement hoặc test?
- Flow này có quá nhỏ để cần use case riêng không?

## Failure Modes / Cách nó gây lỗi

- Mô tả quá giống UI script nên mất business goal
- Chỉ viết happy path nên bỏ sót exception quan trọng
- Gộp quá nhiều goal vào một use case làm scope phình
- Không gắn acceptance criteria nên flow khó nghiệm thu

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần use case formal cho CRUD đơn giản đã rõ bằng API contract hoặc story nhỏ
- Dễ over-engineer nếu biến mọi click thành use case riêng

## Gồm những gì

- [[Acceptance Criteria]]

## Nối mạnh

- [[Stakeholder]] vì stakeholder/actor quyết định goal và success condition của use case
- [[Functional Requirement]] vì use case thường triển khai hoặc nhóm các functional requirement
- [[User Story]] vì cả hai đều mô tả nhu cầu theo góc nhìn người dùng nhưng khác độ chi tiết

## Liên quan rộng

- Business process modeling
- UX flow
- Scenario testing

## Keywords / Từ khóa tìm kiếm

- Use Case
- usage scenario
- ca sử dụng
- use
- case
- Requirement
- Planning

## Source trace

- Software Requirements 3rd Ed Ch08
