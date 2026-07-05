# Test Coverage

Aliases: coverage, độ phủ test

Type: Testing / Verification

## Context / Ngữ cảnh

Test Coverage xuất hiện khi team muốn biết phần code nào đã được test chạm tới và phần nào chưa. Nó thường dùng trong unit/integration test, CI quality gate, refactor lớn, legacy code cleanup và review risk của code path chưa được kiểm chứng.

## Boundary / Ranh giới

### Nó là gì

Test Coverage là metric đo code được test thực thi theo line, branch, function, statement hoặc condition. Nó là tín hiệu giúp phát hiện vùng chưa có test, không phải bằng chứng behavior đúng. Coverage tốt cần đi kèm assertion chất lượng và test case có ý nghĩa.

### Nó không phải là gì

Coverage cao không có nghĩa hệ thống đúng. Test có thể chạy qua dòng code nhưng assertion yếu hoặc thiếu edge case. Coverage cũng không thay thế test design; chạy 90% line coverage vẫn có thể bỏ sót bug ở branch quan trọng, integration boundary hoặc business invariant.

## Core Mechanism / Cơ chế lõi

Tool instrument code khi test chạy, ghi lại line/branch/function nào được execute, rồi tạo report theo file/module. Team dùng report để phát hiện untested area, đặt threshold hợp lý và ưu tiên coverage cho code critical thay vì ép mọi file đạt cùng con số.

## Project Role / Vai trò trong dự án

Test Coverage giúp review PR và legacy module bằng câu hỏi: logic quan trọng có test nào chạm tới chưa. Nó hữu ích khi refactor service layer, validation, transaction, security rule hoặc algorithm. Nó nên được dùng như bản đồ rủi ro, không phải chỉ tiêu hình thức.

## Output / Artifact nên có

- Coverage report theo line/branch/function
- Threshold policy theo module hoặc project
- Gap list cho code critical chưa có test
- PR coverage diff nếu CI hỗ trợ
- Note cho phần intentionally uncovered như glue/config/generated code

## Decision Checklist / Câu hỏi kiểm tra

- Coverage đang đo line, branch, function hay condition?
- Code critical có branch coverage đủ chưa?
- Test có assertion mạnh hay chỉ chạy qua code?
- Threshold có khiến team viết test rỗng để qua gate không?
- File generated/config có nên exclude không?
- Coverage gap nào ảnh hưởng release risk nhất?
- Coverage diff trong PR có giảm mạnh ở module quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Đuổi theo % coverage làm test nhiều nhưng assertion yếu.
- Line coverage cao nhưng branch/error path không test.
- Threshold quá cứng làm dev thêm test hình thức hoặc ignore gate.
- Coverage exclude quá rộng che vùng risk thật.
- Coverage chỉ unit test nên integration/security path vẫn mù.
- Báo cáo coverage không chạy trong CI nên nhanh chóng lỗi thời.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype ngắn hạn có thể chưa cần coverage gate formal.
- Không nên đặt target cao đồng loạt cho legacy repo nếu chưa có chiến lược cải thiện.
- Không nên dùng coverage làm metric duy nhất để đánh giá chất lượng test.

## Gồm những gì

- [[Unit Test]]
- [[White Box Testing]]

## Nối mạnh

- [[Unit Test]] vì coverage thường được đo mạnh nhất ở unit test suite.
- [[Regression Test]] vì coverage gap có thể chỉ ra nơi cần regression guard.
- [[CI]] vì coverage report/gate nên chạy tự động.
- [[Assertion]] vì coverage chỉ có ý nghĩa khi assertion đủ mạnh.
- [[Integration Test]] vì line coverage không thay thế integration boundary test.

## Liên quan rộng

- Quality metrics
- Test strategy
- Legacy refactor
- CI quality gate

## Keywords / Từ khóa tìm kiếm

- Test Coverage
- coverage
- độ phủ test
- line coverage
- branch coverage
- function coverage
- statement coverage
- coverage threshold
- coverage report
- coverage gap
- PR coverage diff
- test quality
- coverage debugging

## Source trace

- Software Testing ISTQB Map
- xUnit Test Patterns
