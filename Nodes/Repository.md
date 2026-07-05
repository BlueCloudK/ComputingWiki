# Repository

Aliases: repository pattern, mẫu repository

Type: Code Design / Pattern

## Context / Ngữ cảnh

Repository xuất hiện khi codebase cần tách domain/service logic khỏi chi tiết persistence như SQL, ORM, external API hoặc storage. Nó thường gặp trong backend có use case phức tạp, cần unit test domain/service, hoặc muốn gom query liên quan tới một aggregate/resource vào boundary rõ.

## Boundary / Ranh giới

### Nó là gì

Repository là pattern tạo abstraction cho việc truy xuất và lưu trữ object/aggregate/resource. Thay vì controller/service viết SQL/ORM query rải rác, repository expose interface như `findById`, `save`, `exists`, `findByEmail` và che chi tiết database/storage phía sau.

### Nó không phải là gì

Repository không phải lớp bắt buộc trong mọi app. Nếu nó chỉ wrap ORM một-một mà không giảm coupling, không gom rule query và không giúp test, nó chỉ thêm indirection. Repository cũng không nên chứa business workflow chính; workflow vẫn nên nằm ở service/use case/domain layer.

## Core Mechanism / Cơ chế lõi

Service/use case phụ thuộc vào repository interface. Implementation của repository dùng ORM/SQL/API/storage để load/save dữ liệu. Boundary tốt giữ query/persistence details ở repository, còn business decision ở service/domain. Test có thể mock/fake repository khi không cần database thật.

## Project Role / Vai trò trong dự án

Repository là node cần mở khi controller/service đang đầy query, unit test khó vì dính database, hoặc nhiều nơi viết cùng logic truy xuất dữ liệu. Nó giúp team quyết định query nào nên gom, interface nên nhỏ tới đâu và khi nào abstraction đang quá mức.

## Output / Artifact nên có

- Repository interface/module với responsibility rõ
- Method list theo use case thật, không expose query builder tùy tiện
- Implementation detail: ORM/SQL/storage/API phía sau
- Test strategy: fake/mock repository hoặc integration test với database thật
- Refactor note nếu gom query rải rác vào repository

## Decision Checklist / Câu hỏi kiểm tra

- Repository này che persistence detail nào khỏi service/domain?
- Method có phản ánh use case/domain language hay chỉ wrap CRUD máy móc?
- Business rule có bị nhét vào repository sai layer không?
- Interface có quá rộng hoặc leak ORM/query builder không?
- Test cần mock/fake repository hay nên dùng integration test database thật?
- Có nhiều implementation thật không, hay abstraction chỉ để “cho đẹp”?
- Transaction boundary nằm ở service/use case hay repository, và có rõ không?

## Failure Modes / Cách nó gây lỗi

- Repository chỉ wrap ORM CRUD một-một làm code nhiều lớp nhưng không rõ hơn.
- Business logic bị giấu trong query/repository khiến service nhìn đơn giản giả.
- Interface quá generic làm mọi nơi truyền condition tùy tiện và mất boundary.
- Repository che mất query performance, N+1 hoặc transaction behavior.
- Mock repository quá nhiều làm test pass nhưng integration với database fail.
- Transaction boundary mơ hồ khi nhiều repository cùng được gọi trong một use case.

## Khi nào chưa cần hoặc dễ over-engineer

- CRUD nhỏ, logic đơn giản và ORM đã đủ rõ có thể chưa cần repository riêng.
- Không nên tạo repository cho mọi table nếu chưa có use case/query phức tạp.
- Không nên dùng repository để né việc hiểu SQL, transaction và query plan.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Service Layer]] vì service/use case thường gọi repository để truy cập dữ liệu.
- [[ORM]] vì repository hay bọc ORM để giảm coupling với persistence detail.
- [[Transaction]] vì nhiều repository call trong một use case cần transaction boundary rõ.
- [[Unit Test]] vì repository abstraction thường nhằm tăng testability.
- [[Dependency Injection]] vì repository implementation thường được inject vào service.

## Liên quan rộng

- Codebase
- Refactoring
- Maintainability
- Domain modeling

## Keywords / Từ khóa tìm kiếm

- Repository
- repository pattern
- mẫu repository
- persistence abstraction
- data access layer
- DAO
- repository interface
- fake repository
- ORM repository
- query boundary
- service repository
- repository pattern debugging

## Source trace

- Patterns of Enterprise Application Architecture
- Domain-Driven Design references
