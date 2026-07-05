# Unit Test

Aliases: unit testing, kiểm thử đơn vị

Type: Testing / Verification

## Context / Ngữ cảnh

Unit Test xuất hiện khi cần kiểm tra một đơn vị code nhỏ như function, class, method, service use case hoặc domain rule trong isolation tương đối. Nó giúp bắt lỗi logic sớm, bảo vệ refactor và ghi lại expectation của behavior quan trọng.

## Boundary / Ranh giới

### Nó là gì

Unit Test là test tập trung vào một unit nhỏ với input, expected output/side effect và dependency được kiểm soát bằng fake/mock/stub khi cần. Unit tốt thường nhanh, deterministic, chạy trong CI và chỉ fail khi behavior của unit bị phá.

### Nó không phải là gì

Unit Test không chứng minh toàn hệ thống tích hợp đúng. Nếu mock quá sâu hoặc test implementation detail, test có thể pass dù integration thật fail. Unit test cũng không thay thế integration/system/acceptance test cho database, network, UI hoặc contract nhiều service.

## Core Mechanism / Cơ chế lõi

Test setup tạo input và dependency giả hoặc in-memory, gọi unit cần kiểm tra, rồi assertion output/state/interaction quan trọng. Unit test tốt theo pattern arrange-act-assert, cover happy path, edge case, failure path và regression bug quan trọng.

## Project Role / Vai trò trong dự án

Unit Test là node cần mở khi refactor service/domain logic, sửa bug logic, thêm validation/rule hoặc muốn CI bắt regression nhanh. Nó giúp team tự tin thay đổi code mà không cần chạy toàn bộ app thủ công mỗi lần.

## Output / Artifact nên có

- Test case rõ input, expected output và reason/risk được cover
- Test data cho happy path, boundary value, invalid input và failure path
- Mock/fake/stub policy cho dependency ngoài unit
- Regression test gắn với bug đã từng xảy ra
- CI rule chạy unit test nhanh trên mỗi PR/commit quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Unit này là function/class/service/domain rule nào?
- Test đang bắt logic behavior hay chỉ test implementation detail?
- Dependency nào nên fake/mock, dependency nào nên dùng integration test?
- Có edge case và failure path quan trọng chưa?
- Test có deterministic, nhanh và không phụ thuộc network/time/random thật không?
- Khi refactor không đổi behavior, test có vẫn pass không?
- Có bug cũ nào cần regression test không?

## Failure Modes / Cách nó gây lỗi

- Test chỉ cover happy path nên production vẫn lỗi edge case.
- Mock quá sâu làm test pass nhưng integration với database/API fail.
- Test implementation detail khiến refactor hợp lệ cũng phá test.
- Flaky test do time/random/thread/network làm team mất niềm tin CI.
- Assertion quá yếu chỉ kiểm tra “không throw” nên không bắt sai behavior.
- Unit test nhiều nhưng thiếu integration test nên contract giữa module vẫn vỡ.

## Khi nào chưa cần hoặc dễ over-engineer

- Spike/prototype bỏ đi rất nhanh có thể chưa cần test automation đầy đủ.
- Không nên unit test getter/setter hoặc code quá đơn giản không có risk.
- Không nên mock mọi thứ nếu behavior cần kiểm chứng nằm ở integration boundary.

## Gồm những gì

- [[Assertion]]
- [[Mock]]
- [[Test Coverage]]

## Nối mạnh

- [[Regression Test]] vì unit test thường lưu lại bug fix thành regression guard.
- [[Service Layer]] vì service use case thường là nơi unit test workflow tốt.
- [[Repository]] vì repository thường được fake/mock khi unit test service.
- [[Dependency Injection]] vì DI giúp thay dependency trong unit test.
- [[Validation]] vì validation rule có thể test bằng unit test nhanh.

## Liên quan rộng

- Quality assurance
- CI/CD
- Refactoring safety
- Developer feedback loop

## Keywords / Từ khóa tìm kiếm

- Unit Test
- unit testing
- kiểm thử đơn vị
- arrange act assert
- test double
- mock
- fake
- stub
- assertion
- regression test
- deterministic test
- flaky test
- test isolation
- unit test debugging

## Source trace

- Software Testing ISTQB Map
- xUnit Test Patterns
