# Service Level Objective

Aliases: SLO, mục tiêu mức dịch vụ

Type: Reliability / SRE

## Context / Ngữ cảnh

Service Level Objective xuất hiện khi team cần định nghĩa “service đủ tốt” bằng mục tiêu đo được thay vì cảm giác ổn định chung chung. SLO thường áp dụng cho user journey quan trọng như login, checkout, API read/write, job completion hoặc AI inference response.

## Boundary / Ranh giới

### Nó là gì

SLO là mục tiêu reliability cụ thể cho một Service Level Indicator trong một time window, ví dụ 99.9% request thành công trong 30 ngày hoặc p95 latency dưới 300ms cho endpoint quan trọng. Nó giúp cân bằng tốc độ release và độ ổn định bằng error budget.

### Nó không phải là gì

SLO không phải mọi metric đẹp trên dashboard. Nếu metric không phản ánh user impact hoặc không ảnh hưởng quyết định release/incident, nó không phải SLO tốt. SLO cũng không phải SLA pháp lý với khách hàng, dù SLA có thể dựa trên SLO nội bộ.

## Core Mechanism / Cơ chế lõi

Team chọn SLI đại diện trải nghiệm user, đặt objective trong một window, tính phần lỗi được phép thành error budget, rồi dùng burn rate để cảnh báo và điều chỉnh release. SLO tốt cần rõ numerator/denominator, scope, exclusions, data source và owner.

## Project Role / Vai trò trong dự án

SLO giúp quyết định khi nào được tiếp tục release, khi nào phải dừng feature work để sửa reliability, và alert nào thật sự đáng gọi người. Nó là cầu nối giữa monitoring kỹ thuật và impact sản phẩm.

## Output / Artifact nên có

- SLI definition: success/failure, latency, availability hoặc freshness metric
- SLO target và time window: ví dụ 99.9% trong 30 ngày
- Error budget calculation và burn-rate alert
- Dashboard theo user journey/service critical path
- Policy khi budget burn nhanh hoặc budget cạn: freeze release, rollback, reliability work

## Decision Checklist / Câu hỏi kiểm tra

- SLO này đo user journey nào?
- SLI có phản ánh user impact thật không?
- Numerator/denominator và data source có rõ không?
- Target có thực tế không hay đặt 100% không thể đạt?
- Time window phù hợp với business/user expectation không?
- Error budget có ảnh hưởng quyết định release không?
- Alert burn-rate có phát hiện nhanh nhưng không quá noisy không?

## Failure Modes / Cách nó gây lỗi

- SLO đặt theo CPU/RAM thay vì user impact nên tối ưu sai chỗ.
- Target quá cao làm team bị khóa release không cần thiết.
- Target quá thấp làm user bị ảnh hưởng nhưng budget vẫn “ổn”.
- SLI tính sai denominator nên lỗi thật không được tính.
- SLO không gắn policy nên chỉ là con số trang trí.
- Không tách critical journey làm lỗi nhỏ và lỗi lớn bị cân như nhau.

## Khi nào chưa cần hoặc dễ over-engineer

- Service chưa có user thật có thể bắt đầu bằng vài metric/alert cơ bản trước.
- Không nên tạo quá nhiều SLO cho mọi endpoint; ưu tiên journey quan trọng.
- Không nên đặt SLO nếu chưa có dữ liệu baseline và owner hành động.

## Gồm những gì

- [[Error Budget]]
- [[Monitoring]]

## Nối mạnh

- [[Monitoring]] vì SLO cần telemetry đáng tin để tính SLI.
- [[Error Budget]] vì error budget là phần lỗi được phép theo SLO.
- [[Alert]] vì burn-rate alert thường dựa trên SLO.
- [[Incident]] vì SLO breach thường kích hoạt incident hoặc reliability work.

## Liên quan rộng

- Reliability target
- User journey metrics
- Release governance
- SLA

## Keywords / Từ khóa tìm kiếm

- Service Level Objective
- SLO
- mục tiêu mức dịch vụ
- SLI
- Service Level Indicator
- error budget
- burn rate
- availability SLO
- latency SLO
- reliability target
- user journey metric
- SLO dashboard
- SLO alert
- SLO debugging

## Source trace

- Google SRE Book
- SRE Workbook SLO chapters
