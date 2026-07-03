# Design Patterns

Aliases: GoF patterns, mẫu thiết kế

Type: Code Design / Pattern

## Bản chất

Design Patterns là cách tổ chức responsibility, dependency hoặc variation trong code. Nó chỉ có giá trị khi làm code dễ đổi, dễ test hoặc giảm coupling; nếu dùng vì tên pattern nghe hay thì thường làm code khó đọc hơn. Nó nối với các phần liên quan như [[Design Pattern]], [[Creational Pattern]], [[Structural Pattern]] và nhóm quyết định quanh design patterns.

## Dùng trong dự án để làm gì

Design Patterns là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

## Khi nào cần quan tâm

- Một class/module có quá nhiều trách nhiệm
- Logic bị duplicate giữa nhiều handler/service
- Dependency làm unit test khó viết hoặc mock quá nặng
- Có nhiều biến thể behavior cần thay đổi độc lập

## Output / artifact nên có

- Design decision ngắn ghi pattern/responsibility được chọn
- Interface hoặc module boundary rõ input/output
- Refactor checklist và test regression cho behavior cũ

## Checklist kiểm tra

- Pattern này giải quyết coupling/duplication cụ thể nào?
- Responsibility mới nằm đúng layer chưa?
- Interface có đủ nhỏ và dễ test không?
- Có làm tăng indirection quá mức không?
- Regression test có giữ behavior cũ không?

## Lỗi / rủi ro thường gặp

- Áp pattern máy móc làm code nhiều lớp hơn nhưng không rõ hơn
- Business rule bị giấu sai layer
- Interface quá chung gây leak abstraction
- Refactor thiếu test làm đổi behavior ngoài ý muốn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần pattern khi logic đơn giản và chưa có biến thể thật
- Dễ over-engineer nếu tạo abstraction trước khi thấy duplication hoặc volatility

## Gồm những gì

- [[Design Pattern]]
- [[Creational Pattern]]
- [[Structural Pattern]]
- [[Behavioral Pattern]]
- [[Factory Method]]
- [[Abstract Factory]]
- [[Builder]]
- [[Prototype]]
- [[Singleton]]
- [[Adapter]]
- [[Bridge]]
- [[Composite]]
- [[Decorator]]
- [[Facade]]
- [[Proxy]]
- [[Observer]]
- [[State]]
- [[Strategy]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Design Pattern Map
