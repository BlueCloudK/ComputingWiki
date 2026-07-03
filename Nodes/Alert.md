# Alert

Aliases: alert, cảnh báo

Type: Reliability / SRE

## Bản chất

Alert tập trung vào việc service tiếp tục đáp ứng kỳ vọng qua thời gian, kể cả khi có lỗi, tải tăng hoặc deploy thay đổi. Nó gắn reliability với SLO, error budget, monitoring, incident response và postmortem. Nó nối với các phần liên quan như [[Monitoring]], [[Incident Response]].

## Dùng trong dự án để làm gì

Alert giúp team quyết định khi nào ưu tiên feature, khi nào dừng để giảm risk vận hành. Trong dự án, nó biến 'ổn định' thành tín hiệu đo được và quy trình phản ứng khi service degrade.

## Khi nào cần quan tâm

- Service có user thật và downtime/error gây ảnh hưởng
- Cần đặt SLO, alert hoặc error budget
- Incident lặp lại nhưng chưa có postmortem/action item
- Toil vận hành thủ công tăng theo traffic

## Output / artifact nên có

- SLO/SLI hoặc reliability metric được owner chấp nhận
- Alert rule, runbook và incident response checklist
- Postmortem/action item sau incident quan trọng

## Checklist kiểm tra

- User-visible reliability được đo bằng metric nào?
- Alert có actionable hay chỉ tạo noise?
- Error budget có ảnh hưởng quyết định release không?
- Runbook có giúp người trực xử lý trong incident không?
- Postmortem có action item giảm recurrence không?

## Lỗi / rủi ro thường gặp

- Alert fatigue làm team bỏ qua tín hiệu thật
- SLO đặt sai nên tối ưu không khớp user impact
- Incident không có learning nên lỗi lặp lại
- Automation thiếu kiểm soát gây blast radius lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần SRE process nặng cho service chưa có user thật
- Dễ over-engineer nếu đặt quá nhiều SLO/alert trước khi biết user journey quan trọng

## Gồm những gì

- [[Monitoring]]
- [[Incident Response]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- SRE Map / monitoring/alerting
