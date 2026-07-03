# Performance

Aliases: scalability, performance, hiệu năng

Type: Reliability / SRE

## Context / Ngữ cảnh

Performance xuất hiện khi service có user thật và lỗi/downtime làm giảm trải nghiệm hoặc gây chi phí vận hành.

## Boundary / Ranh giới

### Nó là gì

Performance là cách biến 'ổn định' thành metric, SLO, alert, runbook và postmortem/action item.

### Nó không phải là gì

Nó không phải nhiều dashboard cho đẹp; nếu alert không actionable hoặc không gắn user impact thì chỉ tạo noise.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là SLI/SLO + error budget + monitoring + incident response + learning loop. Reliability được đo, cảnh báo, xử lý và cải thiện qua postmortem.

## Project Role / Vai trò trong dự án

Performance là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

## Output / Artifact nên có

- SLO/SLI hoặc reliability metric được owner chấp nhận
- Alert rule, runbook và incident response checklist
- Postmortem/action item sau incident quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- User-visible reliability được đo bằng metric nào?
- Alert có actionable hay chỉ tạo noise?
- Error budget có ảnh hưởng quyết định release không?
- Runbook có giúp người trực xử lý trong incident không?
- Postmortem có action item giảm recurrence không?

## Failure Modes / Cách nó gây lỗi

- Alert fatigue làm team bỏ qua tín hiệu thật
- SLO đặt sai nên tối ưu không khớp user impact
- Incident không có learning nên lỗi lặp lại
- Automation thiếu kiểm soát gây blast radius lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần SRE process nặng cho service chưa có user thật
- Dễ over-engineer nếu đặt quá nhiều SLO/alert trước khi biết user journey quan trọng

## Gồm những gì

- [[Benchmark]]
- [[Profiling]]
- [[Bottleneck]]
- [[Cache]]
- [[Queue]]
- [[Load Test]]
- [[Latency]]
- [[Throughput]]
- [[Backpressure]]
- [[Tail Latency]]
- [[Saturation]]
- [[Performance Budget]]
- [[Capacity]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Production reliability
- Incident management
- Monitoring
- Release governance

## Keywords / Từ khóa tìm kiếm

- Performance
- scalability
- hiệu năng
- Reliability
- SRE
- mục lục kiến thức
- nhánh kiến thức

## Source trace

- Data Intensive Applications Map
- Computer Organization Map
- SRE Map
