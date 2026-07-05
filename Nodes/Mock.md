# Mock

Aliases: mock object, mock function, đối tượng giả

Type: Testing / Verification

## Context / Ngữ cảnh

Mock xuất hiện khi test cần thay dependency thật bằng object/function giả để kiểm soát behavior, tránh network/database thật hoặc kiểm tra interaction. Nó thường dùng trong unit test service layer, external API client, repository, clock/random, message publisher và side effect khó kiểm soát.

## Boundary / Ranh giới

### Nó là gì

Mock là test double dùng để giả lập dependency và thường kiểm tra dependency có được gọi đúng không. Mock giúp isolate unit đang test, ép dependency trả success/failure/timeout và assert interaction như method called, argument, call count hoặc order nếu quan trọng.

### Nó không phải là gì

Mock không phải dữ liệu giả chung chung và không thay thế integration test. Mock quá sâu có thể làm test pass dù contract thật giữa module đã vỡ. Nếu test mock implementation detail thay vì behavior quan trọng, refactor hợp lệ cũng làm test fail.

## Core Mechanism / Cơ chế lõi

Test tạo mock/fake/stub cho dependency, cấu hình response hoặc expectation, inject vào unit, gọi behavior cần test, rồi assert output/state và interaction cần thiết. Mock tốt nên nằm ở boundary bên ngoài unit, không mock mọi hàm nội bộ chỉ để dễ assert.

## Project Role / Vai trò trong dự án

Mock giúp unit test nhanh, deterministic và không phụ thuộc external system. Nó hữu ích khi test failure path như API timeout, repository throw error, payment declined, queue publish fail hoặc clock ở mốc thời gian cụ thể.

## Output / Artifact nên có

- Mock/stub setup cho dependency ngoài unit
- Expected interaction nếu interaction chính là behavior cần bảo vệ
- Fake implementation nếu cần behavior stateful hơn mock call count
- Test case cho success, failure, timeout, invalid response
- Note dependency nào không nên mock mà cần integration test

## Decision Checklist / Câu hỏi kiểm tra

- Dependency này có cần mock không, hay dùng real/fake tốt hơn?
- Test đang assert behavior hay implementation detail?
- Mock contract có khớp dependency thật không?
- Có integration test nào bảo vệ boundary thật không?
- Mock có làm failure path dễ test hơn không?
- Call count/order có thật sự quan trọng không?
- Mock setup có quá phức tạp so với logic đang test không?

## Failure Modes / Cách nó gây lỗi

- Mock quá sâu làm test pass nhưng integration thật fail.
- Assert call count/order không quan trọng làm refactor khó.
- Mock response không giống API/database thật.
- Mock mọi thứ khiến test chỉ kiểm tra chính mock setup.
- Thiếu integration test nên contract drift không bị bắt.
- Mock singleton/global state không reset làm test phụ thuộc thứ tự.

## Khi nào chưa cần hoặc dễ over-engineer

- Pure function không dependency ngoài thường không cần mock.
- Không nên mock database/API nếu mục tiêu test là mapping/contract thật.
- Không nên tạo mock framework phức tạp khi fake object đơn giản đủ dùng.

## Gồm những gì

- [[Assertion]]

## Nối mạnh

- [[Unit Test]] vì mock thường dùng để isolate unit test.
- [[Integration Test]] vì integration test bù lại blind spot do mock tạo ra.
- [[Dependency Injection]] vì DI giúp inject mock/fake vào unit.
- [[Repository]] vì repository thường được mock/fake khi test service.
- [[Assertion]] vì mock thường đi kèm assertion về interaction hoặc output.

## Liên quan rộng

- Test double
- Stub
- Fake object
- Test isolation

## Keywords / Từ khóa tìm kiếm

- Mock
- mock object
- mock function
- đối tượng giả
- test double
- stub
- fake
- spy
- mock interaction
- call count
- dependency mock
- mocking strategy
- mock debugging

## Source trace

- xUnit Test Patterns
- Software Testing ISTQB Map
