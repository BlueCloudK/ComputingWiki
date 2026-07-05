# Regression Test

Aliases: regression testing, kiểm thử hồi quy

Type: Testing / Verification

## Context / Ngữ cảnh

Regression Test xuất hiện khi cần đảm bảo bug đã sửa hoặc behavior đã ổn định không bị phá lại bởi thay đổi mới. Nó thường được thêm sau incident, bug production, refactor lớn, API change, migration hoặc dependency upgrade.

## Boundary / Ranh giới

### Nó là gì

Regression Test là test được giữ lại để phát hiện lỗi cũ quay lại. Nó có thể ở unit, integration, E2E, contract hoặc snapshot level tùy lỗi từng xảy ra nằm ở đâu. Giá trị của nó nằm ở việc tái hiện risk cụ thể, không phải tăng số lượng test cho đẹp.

### Nó không phải là gì

Regression Test không phải toàn bộ test suite. Không phải bug nào cũng cần E2E regression nặng; chọn level test sai sẽ làm suite chậm/flaky. Regression test cũng không chứng minh hệ thống đúng tuyệt đối, nó chỉ guard một behavior/risk đã biết.

## Core Mechanism / Cơ chế lõi

Khi phát hiện bug, team thu minimal reproduction, xác định expected behavior, viết test fail trước hoặc cùng lúc fix, rồi đưa vào suite chạy định kỳ/CI. Test phải đủ cụ thể để bắt lỗi quay lại nhưng không quá bám implementation khiến refactor hợp lệ cũng fail.

## Project Role / Vai trò trong dự án

Regression Test biến lỗi đã học thành guardrail. Với repo dài hạn, nó giúp tránh cùng một lỗi quay lại sau vài tháng khi context ban đầu đã mất. Nó cũng là artifact tốt để giải thích vì sao một edge case quan trọng tồn tại.

## Output / Artifact nên có

- Regression test case gắn với bug/issue/incident hoặc failure note
- Minimal reproduction input và expected result
- Test level hợp lý: unit/integration/E2E/contract
- CI placement: chạy nhanh trước merge hoặc nightly nếu nặng
- Comment ngắn nếu edge case khó hiểu

## Decision Checklist / Câu hỏi kiểm tra

- Test này bảo vệ bug/failure mode cụ thể nào?
- Level test đã đủ thấp để nhanh và ổn định chưa?
- Test có fail nếu bug cũ quay lại không?
- Test có quá bám implementation không?
- Test data có đại diện đúng edge case không?
- Test có chạy trong CI/regression suite đúng lúc không?
- Nếu test flaky, nó đang che signal hay thật sự bắt race quan trọng?

## Failure Modes / Cách nó gây lỗi

- Bug fix không có regression test nên lỗi quay lại sau refactor.
- Regression test quá rộng thành E2E nặng và flaky.
- Test chỉ assert happy path nên không bắt bug cũ.
- Test name mơ hồ nên người sau không biết risk được bảo vệ.
- Test phụ thuộc dữ liệu/time/order chạy nên fail ngẫu nhiên.
- Xóa regression test vì “không hiểu” làm mất guardrail quan trọng.

## Khi nào chưa cần hoặc dễ over-engineer

- Bug nhỏ ở prototype bỏ đi có thể chỉ cần note hoặc unit test nhẹ.
- Không nên biến mọi bug UI nhỏ thành E2E nếu component/unit test đủ.
- Không nên giữ test flaky lâu; phải sửa hoặc hạ level test.

## Gồm những gì

- [[Unit Test]]
- [[E2E Test]]

## Nối mạnh

- [[Unit Test]] vì regression thường nên nằm ở level thấp nhất bắt được lỗi.
- [[Integration Test]] vì lỗi ở boundary module nên có integration regression.
- [[E2E Test]] vì user journey critical có thể cần E2E regression.
- [[CI]] vì regression suite cần chạy tự động để có giá trị.
- [[Incident]] vì incident nên tạo regression guard nếu có thể.

## Liên quan rộng

- Quality assurance
- CI/CD
- Release confidence
- Bug learning loop

## Keywords / Từ khóa tìm kiếm

- Regression Test
- regression testing
- kiểm thử hồi quy
- regression suite
- bug regression
- minimal reproduction
- bug fix test
- edge case test
- CI regression
- flaky regression test
- regression test debugging

## Source trace

- Software Testing ISTQB Map
- xUnit Test Patterns
