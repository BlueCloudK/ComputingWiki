# Traceability

Aliases: requirements traceability, truy vết yêu cầu

Type: Requirement / Planning

## Context / Ngữ cảnh

Traceability xuất hiện khi cần biết một requirement đang liên quan tới design, code, test, release hoặc decision nào, đặc biệt khi hệ thống lớn lên và thay đổi thường xuyên.

## Boundary / Ranh giới

### Nó là gì

Traceability là khả năng đi theo liên kết từ requirement sang artifact downstream và ngược lại để hiểu nguồn gốc, tác động và coverage.

### Nó không phải là gì

Nó không phải là backlink cho đẹp graph, không phải tài liệu lặp nội dung, và không cần thành ma trận nặng nếu dự án không có rủi ro thay đổi.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là duy trì liên kết có ý nghĩa: source requirement, design decision, implementation unit, test case, defect, release note. Link phải giúp impact analysis hoặc audit, không chỉ tăng số cạnh graph.

## Project Role / Vai trò trong dự án

Traceability giúp trả lời "nếu đổi requirement này thì vỡ gì" và "test nào chứng minh requirement này". Nó đặc biệt quan trọng cho regression, compliance và hệ thống có nhiều dependency.

## Output / Artifact nên có

- Link requirement sang design, code, test hoặc release item liên quan
- Coverage view cho requirement quan trọng
- Impact notes khi change control xảy ra

## Decision Checklist / Câu hỏi kiểm tra

- Requirement này trace tới test nào?
- Design decision nào tồn tại vì requirement này?
- Nếu xóa hoặc đổi requirement, artifact nào bị ảnh hưởng?
- Link này giúp quyết định thật hay chỉ tạo backlink?
- Có requirement quan trọng nào chưa có coverage không?

## Failure Modes / Cách nó gây lỗi

- Đổi requirement nhưng quên sửa test hoặc API contract
- Có nhiều link nhưng không giải thích lý do nên graph nhiễu
- Trace bị cập nhật thủ công quá nặng rồi nhanh chóng stale
- Compliance cần bằng chứng nhưng không truy được từ requirement sang test

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần trace matrix đầy đủ cho project nhỏ ít rủi ro
- Dễ over-engineer nếu link mọi node với nhau nhưng không phục vụ impact analysis

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Requirement]] vì requirement là điểm neo phổ biến nhất của traceability
- [[Change Control]] vì thay đổi cần biết artifact nào bị ảnh hưởng
- [[Test Coverage]] vì coverage là một dạng trace từ requirement sang kiểm chứng

## Liên quan rộng

- Impact analysis
- Compliance evidence
- Regression safety

## Keywords / Từ khóa tìm kiếm

- Traceability
- requirements traceability
- truy vết yêu cầu
- Traceability learning keyword
- Traceability debug keyword
- Traceability design keyword

## Source trace

- Software Requirements 3rd Ed Ch29
