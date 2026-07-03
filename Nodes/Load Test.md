# Load Test

Aliases: test under load, kiểm thử tải

Type: Testing / Verification

## Context / Ngữ cảnh

Load Test xuất hiện khi cần chứng minh một behavior, artifact hoặc thay đổi kỹ thuật đúng như mong đợi. Nó nằm trong test level, CI, regression, test data và review flow.

## Boundary / Ranh giới

### Nó là gì

Load Test là cơ chế kiểm tra một loại rủi ro cụ thể: logic sai, tích hợp vỡ, regression, dữ liệu test lệch hoặc behavior không khớp expectation.

### Nó không phải là gì

Nó không phải bằng chứng tuyệt đối rằng hệ thống đúng; test luôn có phạm vi, false positive/false negative và blind spot.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chọn test level phù hợp, chuẩn bị test data đại diện, xác định expected result và đưa check vào CI/regression khi rủi ro lặp lại.

## Project Role / Vai trò trong dự án

Load Test gắn code change với bằng chứng kiểm tra, giúp team quyết định merge/release dựa trên tín hiệu thay vì cảm giác.

## Output / Artifact nên có

- Test case hoặc checklist rõ input, expected result và level test
- Test data cho happy path, edge case và failure case
- CI/regression rule cho luồng quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Test này bắt loại lỗi nào và không bắt loại lỗi nào?
- Nó thuộc unit, integration, system hay acceptance level?
- Test data có đủ edge case và dữ liệu lỗi không?
- False positive/false negative có dễ xảy ra không?
- Có chạy trong CI/regression suite đúng thời điểm không?

## Failure Modes / Cách nó gây lỗi

- Test chỉ cover happy path nên production vẫn lỗi edge case
- Mock quá sâu làm test pass nhưng integration fail
- Flaky test làm team mất niềm tin vào CI
- Thiếu regression nên bug cũ quay lại

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần test automation nặng cho spike bỏ đi hoặc prototype rất ngắn
- Dễ over-engineer nếu test chi tiết implementation khiến refactor nào cũng vỡ test

## Gồm những gì

- [[Benchmark]]
- [[Monitoring]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Quality assurance
- CI/CD
- Regression safety
- Release confidence

## Keywords / Từ khóa tìm kiếm

- Load Test
- test under load
- kiểm thử tải
- load
- test
- Testing
- Verification
- kiểm thử
- kiểm thử phần mềm

## Source trace

- SRE Map / Performance maps
