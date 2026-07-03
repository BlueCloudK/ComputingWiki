# Requirement

Aliases: software requirement, yêu cầu phần mềm

Type: Requirement / Planning

## Context / Ngữ cảnh

Requirement xuất hiện khi một nhu cầu, ràng buộc hoặc hành vi mong muốn cần được ghi lại đủ rõ để team có thể thiết kế, triển khai, kiểm thử và quản lý thay đổi.

## Boundary / Ranh giới

### Nó là gì

Requirement là phát biểu có thể kiểm chứng về thứ hệ thống phải làm, chất lượng phải đạt, hoặc ràng buộc phải tuân theo trong một phạm vi nhất định.

### Nó không phải là gì

Nó không phải là ý tưởng mơ hồ, không phải solution design sẵn, và không phải task implementation nếu chưa nói điều kiện cần đạt.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là ghi lại nguồn yêu cầu, stakeholder, phạm vi, rationale, tiêu chí kiểm chứng và trace sang design/test. Requirement tốt giảm khoảng trống diễn giải giữa người cần và người xây.

## Project Role / Vai trò trong dự án

Requirement là đơn vị neo cho scope, design decision, test coverage và change control. Khi requirement đổi, các artifact phụ thuộc phải được kiểm tra theo.

## Output / Artifact nên có

- Requirement statement rõ actor, điều kiện, hành vi hoặc ràng buộc
- Rationale, owner/source và priority nếu cần
- Acceptance criteria hoặc trace sang test/design

## Decision Checklist / Câu hỏi kiểm tra

- Requirement này đến từ stakeholder, luật, hệ thống hay constraint nào?
- Có thể kiểm chứng bằng test, review hoặc metric không?
- Nó là functional hay nonfunctional requirement?
- Out-of-scope và assumption đã rõ chưa?
- Khi requirement đổi, artifact nào phải cập nhật?

## Failure Modes / Cách nó gây lỗi

- Requirement bị viết như mong muốn nên mỗi người hiểu một kiểu
- Trộn problem với solution làm khóa sớm thiết kế
- Không có source/owner nên khó quyết định khi conflict
- Không trace sang test nên thay đổi làm vỡ hành vi mà không biết

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần formal hóa dày khi chỉ đang khám phá problem space
- Dễ over-engineer nếu mọi note ý tưởng đều bị biến thành requirement có quy trình nặng

## Gồm những gì

- [[Functional Requirement]]
- [[Nonfunctional Requirement]]
- [[Acceptance Criteria]]

## Nối mạnh

- [[Scope]] vì requirement quyết định phần nào nằm trong hoặc ngoài phạm vi
- [[Traceability]] vì requirement cần liên kết sang design, code, test và release
- [[Stakeholder]] vì requirement phải có nguồn nhu cầu hoặc người chịu ảnh hưởng

## Liên quan rộng

- Product discovery
- Software specification
- Change management

## Keywords / Từ khóa tìm kiếm

- Requirement
- requirement acceptance
- requirement traceability
- phân tích yêu cầu
- yêu cầu
- software requirement
- yêu cầu phần mềm
- Functional Requirement
- Nonfunctional Requirement
- Acceptance Criteria

## Source trace

- Requirements Engineering - A Good Practice Guide Ch01 / Software Requirements 3rd Ed Ch01
