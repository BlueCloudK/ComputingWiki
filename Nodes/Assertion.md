# Assertion

Aliases: test assertion, câu kiểm tra

Type: Testing / Verification

## Context / Ngữ cảnh

Assertion xuất hiện trong test khi cần nói rõ điều gì phải đúng sau khi chạy code hoặc một hành động. Nó là phần biến test từ “chạy không lỗi” thành bằng chứng có expected result cụ thể.

## Boundary / Ranh giới

### Nó là gì

Assertion là câu kiểm tra trong test để so sánh actual result với expected result: value, state, exception, response, persisted data, side effect hoặc interaction. Assertion tốt phải bám vào behavior quan trọng của người dùng/hệ thống.

### Nó không phải là gì

Assertion không phải chỉ gọi function rồi hy vọng không throw. Assertion yếu làm test pass dù behavior sai. Assertion cũng không nên bám quá sâu vào implementation detail nếu mục tiêu là bảo vệ behavior bên ngoài.

## Core Mechanism / Cơ chế lõi

Test arrange input/context, act bằng cách gọi unit/endpoint/flow, rồi assert output hoặc side effect. Assertion có thể kiểm tra equality, containment, type, error, snapshot, mock interaction, database state, emitted event hoặc UI visible state. Khi fail, message/diff phải đủ dễ hiểu để debug.

## Project Role / Vai trò trong dự án

Assertion là node cần mở khi test pass nhưng bug vẫn lọt, hoặc khi test fail khó hiểu. Nó giúp team viết test có ý nghĩa hơn: kiểm tra đúng behavior, đúng edge case, đúng invariant và đủ thông tin khi fail.

## Output / Artifact nên có

- Expected result rõ ràng trong test case
- Assertion cho output chính và side effect quan trọng
- Failure message/diff dễ debug
- Negative assertion cho forbidden/error path nếu cần
- Assertion helper nếu domain có invariant lặp lại

## Decision Checklist / Câu hỏi kiểm tra

- Test này đang assert điều gì thật sự quan trọng?
- Assertion có bắt được bug mà test muốn phòng không?
- Có cần assert state trong database/cache/event/log không?
- Assertion có quá chung như “not null” hoặc “status 200” không?
- Assertion có quá bám implementation detail không?
- Khi fail, message có giúp biết sai ở đâu không?
- Có assert cả failure/forbidden path không?

## Failure Modes / Cách nó gây lỗi

- Test chỉ assert không throw nên behavior sai vẫn pass.
- Chỉ assert HTTP 200 nhưng không kiểm tra body/persisted state.
- Snapshot quá lớn làm reviewer không thấy change nguy hiểm.
- Assertion bám internal call/order khiến refactor hợp lệ fail.
- Assertion quá nhiều chi tiết không liên quan làm test brittle.
- Failure message mơ hồ khiến debug mất thời gian.

## Khi nào chưa cần hoặc dễ over-engineer

- Exploratory spike có thể chưa cần assertion đầy đủ.
- Không nên assert mọi field nếu chỉ vài field thuộc behavior cần bảo vệ.
- Không nên dùng snapshot lớn thay cho assertion domain rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Unit Test]] vì assertion là phần cốt lõi biến unit test thành check có ý nghĩa.
- [[Mock]] vì mock interaction thường cần assertion về call/argument.
- [[Regression Test]] vì regression guard phải assert đúng bug không quay lại.
- [[Test Coverage]] vì coverage cao vẫn vô nghĩa nếu assertion yếu.
- [[E2E Test]] vì E2E cần assert visible outcome và side effect cuối flow.

## Liên quan rộng

- Test design
- Expected result
- Debug feedback
- Quality assurance

## Keywords / Từ khóa tìm kiếm

- Assertion
- test assertion
- câu kiểm tra
- expected result
- actual result
- assert equal
- assert throws
- assertion message
- weak assertion
- snapshot assertion
- test oracle
- assertion debugging

## Source trace

- xUnit Test Patterns
- Software Testing ISTQB Map
