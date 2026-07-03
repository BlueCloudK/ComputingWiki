# Code Design

Aliases: software design, detailed design, thiết kế code

Type: Artifact / Diagram

## Context / Ngữ cảnh

Code Design xuất hiện khi cấu trúc, flow, state hoặc relationship cần được nhìn thấy thay vì chỉ đọc chữ/code. Nó thường hỗ trợ architecture review, requirement clarification hoặc onboarding.

## Boundary / Ranh giới

### Nó là gì

Code Design là artifact biểu diễn một góc nhìn cụ thể của hệ thống để hỗ trợ quyết định.

### Nó không phải là gì

Nó không phải tranh minh họa cho đẹp; nếu không trả lời câu hỏi review nào thì artifact này dễ thành rác tài liệu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chọn đúng abstraction: bỏ bớt chi tiết không cần, giữ boundary/relationship/flow quan trọng, và gắn artifact với decision hoặc checklist.

## Project Role / Vai trò trong dự án

Code Design là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

## Output / Artifact nên có

- Diagram hoặc artifact có scope, version/date và owner rõ
- Legend hoặc note ngắn giải thích ký hiệu quan trọng
- Decision/link tới node liên quan nếu diagram dẫn đến thay đổi thiết kế

## Decision Checklist / Câu hỏi kiểm tra

- Artifact có nói rõ scope và mức abstraction không?
- Các node/edge quan trọng có khớp hệ thống thật không?
- Có bỏ sót actor, external system, database hoặc failure path không?
- Artifact có còn đúng sau thay đổi gần nhất không?
- Người đọc có biết dùng artifact này để ra quyết định gì không?

## Failure Modes / Cách nó gây lỗi

- Diagram đẹp nhưng không khớp production/code thật
- Quá nhiều chi tiết làm mất insight chính
- Thiếu boundary làm người đọc hiểu sai trách nhiệm
- Không version nên dùng nhầm artifact cũ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần vẽ riêng nếu thay đổi nhỏ và code đã đủ rõ
- Dễ over-engineer khi vẽ nhiều view nhưng không view nào phục vụ decision cụ thể

## Gồm những gì

- [[State Machine]]
- [[Design Pattern]]
- [[Refactor]]
- [[Error Handling]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Documentation
- Architecture review
- Onboarding
- System communication

## Keywords / Từ khóa tìm kiếm

- Code Design
- Code Design MOC
- code design map
- mục lục kiến thức
- nhánh kiến thức
- software design
- detailed design
- thiết kế code
- design pattern
- refactoring
- module boundary
- testability
- mẫu thiết kế
- State Machine
- Refactor

## Source trace

- SWEBOK Map
- Software Modeling and Design Map
- Design Pattern Map
