# User Story

Aliases: agile story, câu chuyện người dùng

Type: Requirement / Planning

## Context / Ngữ cảnh

User Story xuất hiện khi team cần ghi một lát cắt nhu cầu nhỏ theo góc nhìn người dùng để đưa vào backlog, thảo luận và giao việc theo vòng lặp ngắn.

## Boundary / Ranh giới

### Nó là gì

User Story là mô tả ngắn về role, goal và value của người dùng, thường được làm rõ bằng conversation và acceptance criteria.

### Nó không phải là gì

Nó không phải là specification đầy đủ, không phải use case chi tiết, và không phải task kỹ thuật nếu không còn user value.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom một nhu cầu nhỏ thành đơn vị có thể thảo luận, estimate và nghiệm thu. Story chỉ đủ tốt khi có value rõ và criteria giúp team biết khi nào xong.

## Project Role / Vai trò trong dự án

User Story giúp backlog bám vào outcome thay vì danh sách việc kỹ thuật. Nó tạo điểm hẹn cho product, dev và QA cùng уточ lại phạm vi nhỏ.

## Output / Artifact nên có

- Role hoặc user group
- Goal và value mong muốn
- Acceptance criteria, note về assumption hoặc dependency

## Decision Checklist / Câu hỏi kiểm tra

- Story này phục vụ role nào?
- Value hoặc outcome của user là gì?
- Story có đủ nhỏ để hoàn thành trong một iteration không?
- Acceptance criteria có khóa nghĩa của story chưa?
- Có đang giấu một technical task không có user value không?

## Failure Modes / Cách nó gây lỗi

- Viết "as a system" cho mọi thứ nên mất góc nhìn user thật
- Story quá to làm estimate và acceptance mơ hồ
- Thiếu acceptance criteria nên dev/test tự suy diễn
- Tách story theo layer kỹ thuật khiến user value không release được

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần user story nếu công việc là research spike hoặc refactor nội bộ không có user-facing slice
- Dễ over-engineer nếu ép mọi technical concern thành câu chuyện người dùng giả

## Gồm những gì

- [[Acceptance Criteria]]

## Nối mạnh

- [[Requirement]] vì user story là cách biểu diễn requirement trong backlog
- [[Use Case]] vì use case có thể làm rõ flow cho story phức tạp
- [[Stakeholder]] vì role trong story cần đại diện cho stakeholder hoặc user thật

## Liên quan rộng

- Agile backlog
- Product discovery
- Iteration planning

## Source trace

- Software Requirements 3rd Ed Ch20
