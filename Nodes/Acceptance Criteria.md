# Acceptance Criteria

Aliases: acceptance condition, tiêu chí chấp nhận

Type: Requirement / Planning

## Context / Ngữ cảnh

Acceptance Criteria xuất hiện khi một requirement, user story hoặc change request cần tiêu chí rõ để biết khi nào được xem là đạt. Nó là điểm thỏa thuận giữa stakeholder, developer và tester trước khi build hoặc nghiệm thu.

## Boundary / Ranh giới

### Nó là gì

Acceptance Criteria là tập điều kiện pass/fail mô tả hành vi, trạng thái, dữ liệu hoặc phản hồi mà hệ thống phải thỏa để một yêu cầu được chấp nhận.

### Nó không phải là gì

Nó không phải là mô tả tính năng chung chung, không phải test plan đầy đủ, và không thay thế requirement gốc nếu requirement vẫn chưa rõ mục tiêu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là biến mong muốn thành điều kiện kiểm chứng được: given context, user action, expected outcome, edge case và điều kiện từ chối. Criteria tốt giúp tester kết luận pass/fail mà không phải đoán ý product.

## Project Role / Vai trò trong dự án

Acceptance Criteria khóa lại nghĩa thực tế của "done". Nó giúp dev biết phải xử lý case nào, QA biết test gì, stakeholder biết mình đang nghiệm thu điều gì.

## Output / Artifact nên có

- Danh sách điều kiện pass/fail cho requirement hoặc user story
- Case chính, case lỗi và rule dữ liệu cần xác nhận
- Mapping sang acceptance test hoặc test case liên quan

## Decision Checklist / Câu hỏi kiểm tra

- Criteria có đủ rõ để tester nói pass/fail không?
- Có nêu input, action, expected result hoặc trạng thái cuối không?
- Edge case quan trọng đã được ghi chưa?
- Stakeholder có đồng ý đây là điều kiện nghiệm thu không?
- Criteria này có thể chuyển thành acceptance test không?

## Failure Modes / Cách nó gây lỗi

- Dev build theo suy đoán vì tiêu chí chấp nhận quá mơ hồ
- QA và product hiểu khác nhau về chữ "xong"
- Criteria chỉ mô tả happy path, bỏ sót lỗi dữ liệu hoặc permission
- Criteria bị viết như checklist UI nhưng không kiểm tra business outcome

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần chi tiết nặng cho spike hoặc prototype dùng để học nhanh
- Dễ over-engineer nếu viết criteria cho mọi chỉnh sửa nhỏ không có rủi ro nghiệm thu

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Requirement]] vì acceptance criteria làm requirement kiểm chứng được
- [[User Story]] vì user story thường cần criteria để tránh chỉ là lời kể mục tiêu
- [[Test Coverage]] vì criteria quan trọng phải được phản ánh trong coverage hoặc test case

## Liên quan rộng

- Product acceptance
- QA workflow
- Release readiness

## Source trace

- Software Requirements 3rd Ed Ch17
