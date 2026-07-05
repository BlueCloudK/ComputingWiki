# E2E Test

Aliases: end-to-end test, kiểm thử đầu cuối, end to end testing

Type: Testing / Verification

## Context / Ngữ cảnh

E2E Test xuất hiện khi cần kiểm tra một user journey hoặc business flow từ đầu tới cuối qua nhiều layer: UI, API, auth, database, queue, external dependency giả lập và deployment environment. Nó thường dùng cho login, checkout, upload, booking, report, admin approval hoặc scan workflow quan trọng.

## Boundary / Ranh giới

### Nó là gì

E2E Test là test mô phỏng hành vi người dùng hoặc client thật đi qua hệ thống gần production nhất có thể. Nó xác nhận các phần đã được nối đúng và user journey chính vẫn chạy được sau deploy/change.

### Nó không phải là gì

E2E Test không phải thay thế unit/integration test. Nó đắt, chậm và dễ flaky hơn nên không nên dùng để kiểm tra mọi branch logic nhỏ. Nếu chỉ dựa vào E2E, khi fail thường khó khoanh vùng lỗi nằm ở frontend, backend, DB, network hay test data.

## Core Mechanism / Cơ chế lõi

Test runner mở browser/API client, chuẩn bị test data, thực hiện flow như user thật, chờ UI/API state ổn định, rồi assert kết quả visible và side effect quan trọng. E2E tốt cần environment ổn định, selector bền, data isolated và retry/wait hợp lý nhưng không che lỗi thật.

## Project Role / Vai trò trong dự án

E2E Test là gate tốt cho critical path trước release. Nó giúp trả lời câu hỏi thực dụng: user còn đăng nhập, thao tác chính, lưu dữ liệu và thấy kết quả đúng không. Nó đặc biệt hữu ích khi nhiều module đều pass test riêng nhưng flow tổng thể vẫn có thể vỡ.

## Output / Artifact nên có

- Danh sách critical journeys cần E2E
- Test script với setup/teardown data rõ
- Stable selector/test id và wait strategy
- Screenshot/video/trace/log khi fail
- CI placement: smoke E2E trước release, full E2E nightly nếu nặng

## Decision Checklist / Câu hỏi kiểm tra

- Journey này có đủ critical để chịu cost E2E không?
- Test data có isolate theo run để tránh đụng nhau không?
- Selector có bền hay phụ thuộc text/layout dễ đổi?
- Test đang chờ condition thật hay sleep cứng?
- Khi fail có artifact đủ debug không?
- Có thể hạ một phần xuống integration/unit test không?
- E2E này chạy ở PR, staging deploy hay nightly?

## Failure Modes / Cách nó gây lỗi

- Test flaky do timing, network, shared data hoặc selector yếu.
- E2E quá nhiều làm CI chậm và team bỏ qua signal.
- Test chỉ click happy path nhưng không assert dữ liệu cuối.
- Fail khó debug vì thiếu screenshot/video/trace/log.
- Environment test khác production quá nhiều nên confidence giả.
- Test phụ thuộc third-party thật làm pipeline fail ngoài kiểm soát.

## Khi nào chưa cần hoặc dễ over-engineer

- Feature nhỏ chưa có user journey critical có thể dùng unit/integration trước.
- Không nên test mọi edge case bằng E2E.
- Không nên chạy full E2E ở mọi commit nếu suite nặng; có thể tách smoke/nightly.

## Gồm những gì

- [[Use Case]]
- [[Acceptance Criteria]]

## Nối mạnh

- [[Integration Test]] vì E2E rộng hơn nhưng không thay thế integration test.
- [[Regression Test]] vì critical journey thường trở thành regression guard.
- [[Acceptance Criteria]] vì E2E nên phản ánh behavior người dùng mong đợi.
- [[CI]] vì smoke E2E thường chạy trong pipeline.
- [[Deployment]] vì E2E sau deploy xác minh environment thật.

## Liên quan rộng

- Browser automation
- Release confidence
- User journey
- Smoke testing

## Keywords / Từ khóa tìm kiếm

- E2E Test
- end-to-end test
- kiểm thử đầu cuối
- e2e testing
- browser automation
- Playwright
- Cypress
- critical user journey
- smoke E2E
- flaky E2E
- test artifact
- E2E debugging

## Source trace

- Software Testing ISTQB Map
- Playwright documentation
- Cypress documentation
