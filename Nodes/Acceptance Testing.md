# Acceptance Testing

Aliases: acceptance testing, acceptance test, kiểm thử chấp nhận

Type: Testing / Verification

## Bản chất

Acceptance Testing là cách kiểm tra một loại rủi ro cụ thể trong phần mềm: logic sai, tích hợp vỡ, regression, dữ liệu test lệch hoặc behavior không khớp expectation. Nó phải nói rõ bắt lỗi gì và ở test level nào. Nó nối với các phần liên quan như [[Acceptance Criteria]], [[Use Case]] và nhóm quyết định quanh acceptance testing.

## Dùng trong dự án để làm gì

Acceptance Testing giúp chọn test data, test level, CI gate và regression suite để giảm lỗi trước khi release. Trong dự án, nó gắn code change với bằng chứng kiểm tra thay vì chỉ dựa vào cảm giác.

## Khi nào cần quan tâm

- Chuẩn bị merge/release thay đổi có rủi ro
- Bug cũ quay lại hoặc behavior mới chưa chắc đúng
- Cần test data đại diện edge case và failure case
- CI báo flaky/false positive hoặc test bỏ sót lỗi thật

## Output / artifact nên có

- Test case hoặc checklist rõ input, expected result và level test
- Test data cho happy path, edge case và failure case
- CI/regression rule cho luồng quan trọng

## Checklist kiểm tra

- Test này bắt loại lỗi nào và không bắt loại lỗi nào?
- Nó thuộc unit, integration, system hay acceptance level?
- Test data có đủ edge case và dữ liệu lỗi không?
- False positive/false negative có dễ xảy ra không?
- Có chạy trong CI/regression suite đúng thời điểm không?

## Lỗi / rủi ro thường gặp

- Test chỉ cover happy path nên production vẫn lỗi edge case
- Mock quá sâu làm test pass nhưng integration fail
- Flaky test làm team mất niềm tin vào CI
- Thiếu regression nên bug cũ quay lại

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần test automation nặng cho spike bỏ đi hoặc prototype rất ngắn
- Dễ over-engineer nếu test chi tiết implementation khiến refactor nào cũng vỡ test

## Gồm những gì

- [[Acceptance Criteria]]
- [[Use Case]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Software Testing ISTQB Map / Ch02
