# Requirements

Aliases: software requirements, requirements engineering, yêu cầu phần mềm

Type: Requirement / Planning

## Context / Ngữ cảnh

Requirements xuất hiện khi team cần biến nhu cầu, scope hoặc tiêu chí chấp nhận thành thứ có thể thiết kế, code và test được. Nó nằm giữa stakeholder, product decision, design decision và test plan.

## Boundary / Ranh giới

### Nó là gì

Requirements là một điểm kiểm soát độ rõ của nhu cầu: ai cần gì, điều kiện nào được xem là đạt, và thay đổi đó trace sang design/test nào.

### Nó không phải là gì

Nó không phải là câu mô tả mong muốn chung chung, cũng không phải backlog item không có acceptance criteria hoặc ownership rõ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chuyển mơ hồ thành tiêu chí đo được: scope, assumption, acceptance criteria và traceability. Khi tiêu chí rõ, team biết phải build gì, test gì và khi nào được xem là xong.

## Project Role / Vai trò trong dự án

Requirements là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

## Output / Artifact nên có

- Acceptance criteria hoặc decision note có điều kiện pass/fail
- Trace từ requirement sang design, test và release scope
- Danh sách assumption/open question cần stakeholder xác nhận

## Decision Checklist / Câu hỏi kiểm tra

- Tiêu chí này có đo được bằng test, metric hoặc review không?
- Ai là stakeholder/consumer chịu ảnh hưởng chính?
- Có acceptance criteria đủ rõ để tester kết luận pass/fail chưa?
- Requirement này trace tới design và test case nào?
- Nếu scope đổi, node nào phải cập nhật theo?

## Failure Modes / Cách nó gây lỗi

- Build đúng theo suy đoán của dev nhưng sai nhu cầu thật
- Acceptance mơ hồ làm QA không kết luận được
- Scope creep vì không ghi rõ out-of-scope
- Trace thiếu khiến sửa requirement nhưng quên sửa test/design

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần formal hóa nặng khi chỉ là spike ngắn hoặc prototype bỏ đi
- Dễ over-engineer nếu biến mọi ý tưởng nhỏ thành quy trình requirement đầy đủ

## Gồm những gì

- [[Requirement]]
- [[Use Case]]
- [[User Story]]
- [[Scope]]
- [[Traceability]]
- [[Change Control]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Product planning
- Documentation
- Testing
- Scope management

## Source trace

- SWEBOK Map
- Requirements Engineering Map
