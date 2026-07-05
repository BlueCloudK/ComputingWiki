# Service Layer

Aliases: service layer pattern, mẫu service layer

Type: Code Design / Pattern

## Context / Ngữ cảnh

Service Layer xuất hiện khi backend cần một lớp application/use-case nằm giữa controller/API boundary và domain/persistence. Nó thường dùng để gom workflow nghiệp vụ, transaction boundary, authorization check cấp use case, gọi repository/external service và orchestration nhiều bước.

## Boundary / Ranh giới

### Nó là gì

Service Layer là lớp chứa application operation như `createOrder`, `approveClaim`, `registerUser`, `scanProject`. Nó nhận input đã được controller parse/validate, áp rule use case, gọi domain/repository/integration cần thiết, rồi trả output cho controller/API.

### Nó không phải là gì

Service Layer không phải nơi nhét mọi thứ cho xong. Nếu service chỉ gọi repository một dòng hoặc chứa HTTP/request details, nó không tạo boundary tốt. Service cũng không nên biến thành God Service biết quá nhiều module, quá nhiều workflow và quá nhiều infrastructure detail.

## Core Mechanism / Cơ chế lõi

Controller mỏng nhận request và gọi service method. Service method điều phối rule nghiệp vụ, transaction, repository, external API, event/outbox và error mapping ở mức use case. Repository che persistence detail; controller che HTTP detail; service giữ workflow ứng dụng.

## Project Role / Vai trò trong dự án

Service Layer là node cần mở khi controller phình to, business logic rải rác, transaction boundary mơ hồ, unit test use case khó hoặc nhiều endpoint cần dùng lại cùng workflow. Nó giúp team biết logic nào thuộc API/controller, logic nào thuộc domain, logic nào thuộc application service.

## Output / Artifact nên có

- Service method list theo use case thật, không theo table CRUD máy móc
- Input/output contract nội bộ hoặc DTO mapping rõ
- Transaction boundary và rollback/error policy
- Dependency list: repository, external client, event publisher, validator/policy
- Unit/integration tests cho happy path, failure path và authorization/business rule

## Decision Checklist / Câu hỏi kiểm tra

- Service này đại diện use case nào?
- Controller có còn giữ business logic không?
- Transaction boundary có nằm đúng ở service/use case không?
- Service có đang leak HTTP framework, request object hoặc ORM entity ra ngoài không?
- Dependency có quá nhiều tới mức service thành God Service không?
- Business rule nào nên đưa xuống domain/entity thay vì service?
- Test có chứng minh workflow chính và failure path không?

## Failure Modes / Cách nó gây lỗi

- Controller vẫn chứa workflow chính nên service layer chỉ là hình thức.
- Service quá lớn gom mọi use case và khó test/refactor.
- Transaction mở trong repository riêng lẻ khiến nhiều bước không atomic.
- Service gọi external API trong transaction làm lock giữ lâu.
- Service trả ORM entity trực tiếp làm API contract phụ thuộc persistence model.
- Logic authorization/validation nằm rải rác giữa controller/service/repository gây bypass.

## Khi nào chưa cần hoặc dễ over-engineer

- CRUD rất nhỏ, controller gọi ORM trực tiếp và chưa có workflow phức tạp có thể chưa cần service layer riêng.
- Không nên tạo service cho mọi entity nếu không có use case thật.
- Không nên dùng service layer để né việc đặt boundary domain/repository rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Controller]] vì controller nên mỏng và gọi service cho use case chính.
- [[Repository]] vì service layer thường gọi repository để truy cập dữ liệu.
- [[Transaction]] vì transaction boundary thường nằm ở use case/service layer.
- [[Dependency Injection]] vì service dependency thường được inject để test và thay thế.
- [[Unit Test]] vì service layer là nơi unit test workflow/use case tương đối tốt.

## Liên quan rộng

- Application architecture
- Use case orchestration
- Backend maintainability
- Domain modeling

## Keywords / Từ khóa tìm kiếm

- Service Layer
- service layer pattern
- mẫu service layer
- application service
- use case service
- business workflow
- transaction boundary
- thin controller
- God service
- service repository pattern
- service layer testing
- backend architecture

## Source trace

- Patterns of Enterprise Application Architecture
- Domain-Driven Design references
