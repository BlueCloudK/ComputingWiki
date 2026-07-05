# Integration Test

Aliases: integration testing, kiểm thử tích hợp

Type: Testing / Verification

## Context / Ngữ cảnh

Integration Test xuất hiện khi nhiều module, service, database, queue, filesystem, API hoặc third-party client cần được kiểm tra cùng nhau. Mục tiêu là bắt lỗi ở boundary giữa các phần mà unit test thường mock hoặc bỏ qua.

## Boundary / Ranh giới

### Nó là gì

Integration Test là test xác minh các thành phần thật hoặc gần thật có giao tiếp đúng qua contract, schema, transaction, config, auth, network và error behavior. Nó thường chạy với database test, container dependency, API server, message broker hoặc fake external service có contract rõ.

### Nó không phải là gì

Integration Test không phải E2E full user journey. Nó cũng không thay thế unit test; nếu mọi logic nhỏ đều phải chạy qua integration test, feedback sẽ chậm. Integration test nên tập trung vào boundary rủi ro: DB mapping, API contract, transaction, serialization, auth, queue và external call.

## Core Mechanism / Cơ chế lõi

Test dựng môi trường gồm code đang test và dependency thật/gần thật, chuẩn bị test data, gọi boundary như HTTP endpoint/service method/repository/message handler, rồi assert output, side effect và persisted state. Setup/teardown phải deterministic để tránh flaky test và data leak giữa test case.

## Project Role / Vai trò trong dự án

Integration Test giúp team tự tin rằng controller-service-repository-DB, API contract, migration, config và external adapter không vỡ khi refactor. Nó rất hữu ích cho backend/API/RAG/agent workflow nơi lỗi thường nằm ở chỗ nối giữa module.

## Output / Artifact nên có

- Integration test suite theo boundary quan trọng: API, DB, queue, external adapter
- Test fixture/seed data và teardown rõ ràng
- Test environment config: database/container/service URL, secret test, timeout
- Expected result gồm response, persisted state, emitted event/log nếu quan trọng
- CI rule tách test nhanh/chậm nếu suite nặng

## Decision Checklist / Câu hỏi kiểm tra

- Boundary nào cần kiểm tra thật thay vì mock?
- Dependency nào dùng thật, dependency nào fake/stub?
- Test data có isolate giữa test case không?
- Test có assert side effect trong DB/queue/cache không?
- Test có deterministic hay phụ thuộc time/network/random ngoài kiểm soát?
- Khi fail, log/artifact có đủ debug không?
- Có chạy ở CI đúng thời điểm hay chỉ local?

## Failure Modes / Cách nó gây lỗi

- Mock quá nhiều làm integration test không khác unit test.
- Dùng shared database không cleanup làm test phụ thuộc thứ tự chạy.
- External service thật unstable làm test flaky.
- Test chỉ assert status 200 nhưng không kiểm tra persisted state.
- Suite quá chậm khiến team bỏ qua trước merge.
- Config test khác production quá xa nên không bắt lỗi deploy thật.

## Khi nào chưa cần hoặc dễ over-engineer

- Logic thuần nhỏ nên ưu tiên unit test trước.
- Không nên biến mọi case thành integration test nếu unit test đủ bắt logic.
- Không nên gọi third-party production thật trong CI nếu có sandbox/fake contract tốt hơn.

## Gồm những gì

- [[API Contract]]

## Nối mạnh

- [[Unit Test]] vì integration test bổ sung cho unit test ở boundary giữa module.
- [[E2E Test]] vì E2E kiểm tra journey rộng hơn còn integration test kiểm tra boundary hẹp hơn.
- [[API Contract]] vì integration test thường xác nhận request/response contract.
- [[Regression Test]] vì bug integration quan trọng nên thành regression test.
- [[CI]] vì integration suite thường chạy trong pipeline trước merge/release.

## Liên quan rộng

- Test environment
- Database testing
- Contract testing
- Service integration

## Keywords / Từ khóa tìm kiếm

- Integration Test
- integration testing
- kiểm thử tích hợp
- integration test suite
- test database
- test container
- API integration test
- database integration test
- contract test
- test fixture
- test teardown
- flaky integration test
- integration test debugging

## Source trace

- Software Testing ISTQB Map
- xUnit Test Patterns
