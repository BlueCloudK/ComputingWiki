# Software Modeling and Design

Aliases: software modeling, modeling and design, mô hình hóa và thiết kế phần mềm

Type: Artifact / Diagram

## Context / Ngữ cảnh

Software Modeling and Design xuất hiện khi cấu trúc, flow, state hoặc relationship cần được nhìn thấy thay vì chỉ đọc chữ/code. Nó thường hỗ trợ architecture review, requirement clarification hoặc onboarding.

## Boundary / Ranh giới

### Nó là gì

Software Modeling and Design là artifact biểu diễn một góc nhìn cụ thể của hệ thống để hỗ trợ quyết định.

### Nó không phải là gì

Nó không phải tranh minh họa cho đẹp; nếu không trả lời câu hỏi review nào thì artifact này dễ thành rác tài liệu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chọn đúng abstraction: bỏ bớt chi tiết không cần, giữ boundary/relationship/flow quan trọng, và gắn artifact với decision hoặc checklist.

## Project Role / Vai trò trong dự án

Software Modeling and Design là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

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

- [[UML Notation]]
- [[Software Life Cycle Model]]
- [[Software Design Concept]]
- [[Software Architecture Concept]]
- [[Software Modeling Method]]
- [[Software Modeling]]
- [[Use Case Modeling]]
- [[Static Modeling]]
- [[Dynamic Interaction Modeling]]
- [[Finite State Machine]]
- [[Architectural Design]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Documentation
- Architecture review
- Onboarding
- System communication

## Keywords / Từ khóa tìm kiếm

- Software Modeling and Design
- software modeling and design notation
- software modeling and design review
- mô hình hóa hệ thống
- Software Modeling and Design MOC
- software modeling and design map
- mục lục kiến thức
- nhánh kiến thức
- software modeling
- modeling and design
- mô hình hóa và thiết kế phần mềm
- UML Notation
- Software Life Cycle Model
- Software Design Concept
- Software Architecture Concept

## Source trace

- Software Modeling and Design Map
