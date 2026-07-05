# Matrix Build

Aliases: Matrix Build, matrix build

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Matrix Build xuất hiện khi CI cần chạy cùng một workflow trên nhiều biến thể như OS, runtime version, database version, browser, architecture hoặc feature flag. Nó giúp kiểm tra compatibility mà không copy-paste nhiều job gần giống nhau.

## Boundary / Ranh giới

### Nó là gì

Matrix Build là kỹ thuật sinh nhiều job CI từ một cấu hình tham số. Ví dụ một test suite chạy trên Node 20/22, Ubuntu/Windows/macOS, hoặc nhiều database version. Matrix giúp bao phủ compatibility và phát hiện lỗi chỉ xảy ra ở một tổ hợp môi trường.

### Nó không phải là gì

Matrix Build không phải càng nhiều tổ hợp càng tốt. Matrix quá lớn làm CI chậm, tốn tiền và nhiều flaky signal. Nó cũng không thay thế test design; nếu test rỗng, chạy trên 20 môi trường vẫn không tăng confidence thật.

## Core Mechanism / Cơ chế lõi

Pipeline định nghĩa list variable và job template. CI runner tạo job cho từng combination hoặc include/exclude combination cụ thể. Mỗi job có label, environment, cache key và artifact riêng. Fail-fast, allow-failure hoặc required check cần được quyết định rõ.

## Project Role / Vai trò trong dự án

Matrix Build hữu ích khi project cần hỗ trợ nhiều Node/Python/JDK version, OS, browser hoặc package mode. Nó giúp team biết change có phá môi trường nào không trước khi merge hoặc release.

## Output / Artifact nên có

- Matrix dimensions: OS/runtime/browser/database/version
- Include/exclude rule cho combination có ý nghĩa
- Required/optional job policy
- Cache key có chứa matrix variable cần thiết
- Report/artifact theo từng combination khi fail

## Decision Checklist / Câu hỏi kiểm tra

- Compatibility thật sự cần hỗ trợ là gì?
- Dimension nào quan trọng, dimension nào chỉ làm CI phình?
- Job nào được phép fail, job nào bắt buộc pass?
- Cache key có phân biệt OS/runtime/version không?
- Fail-fast có làm mất thông tin debug các combination khác không?
- Matrix có chạy ở PR hay nightly/release?
- Khi một combination fail, owner xử lý là ai?

## Failure Modes / Cách nó gây lỗi

- Matrix quá lớn làm CI chậm và dev bypass pipeline.
- Cache dùng chung giữa runtime/OS làm build/test sai.
- Required check đặt sai khiến môi trường quan trọng fail nhưng vẫn merge.
- Test flaky chỉ ở một OS/browser làm signal nhiễu.
- Matrix không include version production thật nên confidence giả.
- Artifact/log không tách theo combination nên debug khó.

## Khi nào chưa cần hoặc dễ over-engineer

- Project chỉ support một runtime/OS rõ ràng có thể chưa cần matrix.
- Không nên test mọi version cũ nếu không cam kết support.
- Không nên chạy full matrix ở mọi PR nếu nightly/release matrix đủ cân bằng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì matrix build là pattern phổ biến trong CI pipeline.
- [[GitHub Actions]] vì Actions hỗ trợ matrix strategy trực tiếp.
- [[Test Coverage]] vì matrix mở rộng môi trường test chứ không thay coverage/quality.
- [[Build Cache]] vì cache key phải tương thích từng matrix combination.
- [[Regression Test]] vì matrix giúp bắt regression theo runtime/OS/browser.

## Liên quan rộng

- Compatibility testing
- Multi-runtime support
- CI optimization
- Release confidence

## Keywords / Từ khóa tìm kiếm

- Matrix Build
- matrix build
- CI matrix
- build matrix
- matrix strategy
- multi OS test
- multi version test
- compatibility matrix
- include exclude matrix
- fail fast
- matrix cache key
- matrix build debugging

## Source trace

- GitHub Actions matrix documentation
- Continuous Delivery
