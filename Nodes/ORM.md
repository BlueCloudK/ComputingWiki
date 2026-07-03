# ORM

Aliases: Object Relational Mapper, object-relational mapping, ánh xạ ORM

Type: Backend Engineering / Database

## Context / Ngữ cảnh

ORM xuất hiện khi backend code cần làm việc với relational database thông qua object/entity thay vì viết SQL thủ công ở mọi nơi. Nó thường nằm trong data access layer của web app, service layer, repository pattern hoặc framework như Hibernate, SQLAlchemy, Entity Framework, ActiveRecord.

## Boundary / Ranh giới

### Nó là gì

ORM là lớp ánh xạ giữa object trong code và table/row trong relational database. Nó quản lý entity mapping, query generation, relation loading, change tracking, transaction integration và migration/schema metadata tùy framework.

### Nó không phải là gì

ORM không làm database biến mất. Developer vẫn cần hiểu SQL, index, transaction, isolation, query plan và schema design. ORM cũng không phải luôn tốt hơn raw SQL; với query phức tạp, reporting hoặc performance-critical path, SQL rõ ràng có thể phù hợp hơn.

## Core Mechanism / Cơ chế lõi

ORM map class/entity sang table, field sang column và relation sang foreign key/join. Khi code query hoặc thay đổi entity, ORM sinh SQL, track thay đổi và flush/commit trong transaction. Các cơ chế như lazy loading, eager loading, identity map, unit of work và query builder giúp code gọn hơn nhưng cũng có thể che giấu query thật.

## Project Role / Vai trò trong dự án

ORM ảnh hưởng tới cách team thiết kế data model, repository/service boundary, transaction scope, test data và performance debugging. Khi review backend code dùng ORM, cần nhìn được query sinh ra, relation loading, transaction boundary và chỗ nào nên dùng raw SQL hoặc optimized query.

## Output / Artifact nên có

- Entity mapping rõ ràng: table, primary key, foreign key, relation, cascade rule
- Repository/data access convention: query nào đặt ở đâu, khi nào dùng raw SQL
- Transaction boundary guideline cho service method quan trọng
- SQL logging/profiling setup để debug query ORM sinh ra
- Test hoặc benchmark cho query path quan trọng, đặc biệt list endpoint và relation loading

## Decision Checklist / Câu hỏi kiểm tra

- Entity mapping có khớp schema thật không?
- Relation nào lazy load, relation nào eager load, và tại sao?
- Query quan trọng có được inspect SQL/query plan không?
- Transaction boundary nằm ở service, repository hay framework middleware?
- Cascade delete/update có thể gây mất dữ liệu ngoài ý muốn không?
- ORM có sinh N+1 query ở list endpoint hoặc resolver không?
- Với query phức tạp, raw SQL/view/stored query có rõ hơn ORM abstraction không?

## Failure Modes / Cách nó gây lỗi

- Lazy loading sinh N+1 query làm endpoint chậm khi dữ liệu lớn.
- Transaction boundary mơ hồ làm update một phần hoặc rollback không như mong muốn.
- Cascade rule sai làm xóa/ghi dữ liệu liên quan ngoài ý định.
- ORM query abstraction che SQL thật khiến thiếu index hoặc full scan khó phát hiện.
- Detached entity/change tracking sai làm update bị mất hoặc ghi đè dữ liệu cũ.
- Migration/schema lệch entity mapping làm production fail dù code compile.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ hoặc service chỉ vài query đơn giản có thể dùng SQL/query builder trực tiếp.
- Không nên ép mọi query vào ORM nếu báo cáo/phân tích dữ liệu cần SQL phức tạp rõ ràng.
- Không nên thiết kế entity quá sâu/cascade quá nhiều trước khi domain model và access pattern rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Repository]] vì ORM thường được bọc trong repository/data access layer.
- [[Database Schema]] vì entity mapping phải khớp schema thật.
- [[Database Transaction]] vì ORM thường flush/commit thay đổi trong transaction.
- [[N Plus One Query]] vì lazy loading trong ORM là nguồn phổ biến gây N+1.
- [[Database Migration]] vì schema migration phải đồng bộ với mapping trong code.

## Liên quan rộng

- Backend architecture
- Data modeling
- Query optimization
- Framework conventions

## Keywords / Từ khóa tìm kiếm

- ORM
- Object Relational Mapper
- object-relational mapping
- ánh xạ ORM
- entity mapping
- lazy loading
- eager loading
- change tracking
- unit of work
- identity map
- ORM transaction
- ORM query performance
- Hibernate
- SQLAlchemy
- Entity Framework

## Source trace

- Hibernate documentation
- SQLAlchemy documentation
- Entity Framework Core documentation
