# Quality Attribute

Aliases: quality characteristic, thuộc tính chất lượng

Type: Requirement / Planning

## Context / Ngữ cảnh

Quality Attribute xuất hiện khi cần gọi tên một chiều chất lượng cụ thể của hệ thống để phân tích trade-off, đặt target hoặc thiết kế kiến trúc.

## Boundary / Ranh giới

### Nó là gì

Quality Attribute là thuộc tính như performance, availability, reliability, security, maintainability, scalability, usability hoặc interoperability.

### Nó không phải là gì

Nó không phải là requirement hoàn chỉnh nếu chưa có context và target, cũng không phải một giải pháp kỹ thuật cụ thể.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là tách chất lượng thành attribute có thể thảo luận, đo và trade-off. Mỗi attribute cần stimulus, environment, response và response measure nếu dùng cho kiến trúc.

## Project Role / Vai trò trong dự án

Quality Attribute giúp kiến trúc không chỉ xoay quanh feature. Nó buộc team nói rõ chất lượng nào quan trọng hơn khi có trade-off giữa tốc độ, chi phí, bảo mật và độ dễ bảo trì.

## Output / Artifact nên có

- Tên quality attribute và lý do quan trọng
- Scenario hoặc metric để đo attribute
- Trade-off hoặc architecture decision liên quan

## Decision Checklist / Câu hỏi kiểm tra

- Attribute này có thật sự ảnh hưởng user/business không?
- Có metric hoặc scenario đo được chưa?
- Attribute này xung đột với attribute nào khác?
- Architecture decision nào tồn tại để bảo vệ attribute này?
- Có cần biến attribute này thành NFR cụ thể không?

## Failure Modes / Cách nó gây lỗi

- Dùng từ rộng như "secure" hoặc "scalable" nhưng không có metric
- Tối ưu một attribute và vô tình làm hỏng attribute khác
- Để quality attribute trong tài liệu kiến trúc nhưng không trace sang test/monitoring
- Chọn công nghệ theo buzzword thay vì attribute cần bảo vệ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần taxonomy đầy đủ nếu chỉ đang mô tả feature đơn giản
- Dễ over-engineer nếu phân tích mọi attribute như nhau dù chỉ vài attribute thật sự rủi ro

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Nonfunctional Requirement]] vì NFR cụ thể hóa quality attribute thành target kiểm chứng được
- [[Software Architecture]] vì architecture thường là nơi trade-off quality attribute được quyết định
- [[Scalability]] vì scalability là một quality attribute phổ biến

## Liên quan rộng

- Architecture evaluation
- SLO/SLA design
- Risk analysis

## Keywords / Từ khóa tìm kiếm

- Quality Attribute
- quality characteristic
- thuộc tính chất lượng
- quality
- attribute
- Requirement
- Planning
- chất lượng

## Source trace

- Software Requirements 3rd Ed Ch14 / Software Modeling and Design Map Ch20
