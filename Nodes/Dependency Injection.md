# Dependency Injection

Aliases: DI, inversion of control container, tiêm phụ thuộc

Type: Code Design / Backend

## Context / Ngữ cảnh

Dependency Injection xuất hiện khi một class/module cần dependency như repository, service, logger, HTTP client hoặc config nhưng không nên tự tạo chúng trực tiếp. Nó giúp giảm coupling, tăng testability và làm object graph được cấu hình rõ hơn trong backend/framework.

## Boundary / Ranh giới

### Nó là gì

Dependency Injection là pattern đưa dependency từ bên ngoài vào object, thường qua constructor, method hoặc property. DI container/IoC container có thể tự resolve object graph, quản lý lifetime scope và inject implementation phù hợp theo interface/registration.

### Nó không phải là gì

Dependency Injection không phải magic làm kiến trúc tự sạch. Nếu interface sai boundary, lifetime sai hoặc container config rối, DI chỉ che coupling và làm lỗi runtime khó trace. DI cũng không đồng nghĩa phải tạo interface cho mọi class hoặc dùng framework nặng trong mọi project.

## Core Mechanism / Cơ chế lõi

Thay vì `new` dependency bên trong class, class khai báo dependency cần dùng và nhận từ composition root/container. Container dựa trên registration để chọn implementation, tạo instance, quản lý singleton/scoped/transient lifetime và inject vào consumer. Constructor injection thường rõ ràng nhất vì dependency bắt buộc được biểu hiện ngay trong signature.

## Project Role / Vai trò trong dự án

Dependency Injection ảnh hưởng tới cách backend tổ chức service, repository, adapter, test double và configuration. Khi debug app, DI là nơi kiểm tra implementation nào được inject, lifetime có đúng không, config môi trường có bind đúng không và circular dependency có xuất hiện không.

## Output / Artifact nên có

- Composition root hoặc module registration rõ: interface → implementation
- Lifetime decision: singleton, scoped, transient và lý do
- Test strategy: mock/fake/stub dependency ở boundary nào
- Config binding note cho dependency theo environment
- Debug checklist cho missing registration, wrong implementation, circular dependency và lifetime bug

## Decision Checklist / Câu hỏi kiểm tra

- Dependency này là bắt buộc hay optional, nên inject qua constructor hay cách khác?
- Interface có đại diện boundary thật hay chỉ tạo cho đủ pattern?
- Lifetime có đúng không: singleton có giữ state/request data không?
- Scoped dependency có bị inject vào singleton không?
- Có circular dependency giữa service không?
- Test có thể thay dependency bằng fake/mock mà không đụng network/database thật không?
- Registration có khác dev/staging/prod theo cách kiểm soát được không?

## Failure Modes / Cách nó gây lỗi

- Missing registration làm app fail lúc startup hoặc khi resolve dependency.
- Wrong implementation được inject làm behavior khác môi trường hoặc khác config.
- Singleton giữ state mutable/request-specific gây leak dữ liệu giữa request.
- Scoped/transient lifetime sai làm connection/client bị tạo quá nhiều hoặc bị dispose sai lúc.
- Circular dependency làm container không resolve được hoặc buộc thiết kế vòng phụ thuộc xấu.
- Quá nhiều abstraction/interface làm code khó đọc dù chưa có nhu cầu thay implementation.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ hoặc module rất đơn giản có thể truyền dependency thủ công không cần container.
- Không nên tạo interface cho mọi class nếu không có boundary/test seam/implementation alternative rõ.
- Không nên dùng service locator trá hình vì nó giấu dependency khỏi constructor và làm test khó hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Inversion of Control]] vì DI là cách phổ biến để áp dụng IoC.
- [[Service Layer]] vì service thường nhận repository/adapter qua DI.
- [[Repository]] vì repository thường được inject vào service/use case.
- [[Unit Test]] vì DI giúp thay dependency thật bằng test double.
- [[Circular Dependency]] vì DI container thường phát hiện vòng phụ thuộc giữa object.

## Liên quan rộng

- Backend architecture
- Testability
- Framework configuration
- Object lifecycle

## Keywords / Từ khóa tìm kiếm

- Dependency Injection
- DI
- inversion of control container
- tiêm phụ thuộc
- constructor injection
- DI container
- IoC container
- service registration
- singleton scoped transient
- dependency lifetime
- missing registration
- circular dependency
- test double
- mock dependency
- composition root

## Source trace

- Martin Fowler Dependency Injection
- .NET Dependency Injection documentation
- Spring Framework dependency injection documentation
