# Reliability

Aliases: reliability, độ tin cậy

Type: Reliability / SRE

## Context / Ngữ cảnh

Reliability xuất hiện khi service có user thật và lỗi/downtime làm giảm trải nghiệm hoặc gây chi phí vận hành.

## Boundary / Ranh giới

### Nó là gì

Reliability là cách biến 'ổn định' thành metric, SLO, alert, runbook và postmortem/action item.

### Nó không phải là gì

Nó không phải nhiều dashboard cho đẹp; nếu alert không actionable hoặc không gắn user impact thì chỉ tạo noise.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là SLI/SLO + error budget + monitoring + incident response + learning loop. Reliability được đo, cảnh báo, xử lý và cải thiện qua postmortem.

## Project Role / Vai trò trong dự án

Reliability ảnh hưởng tới quyết định release, ưu tiên technical debt, incident response và automation giảm toil.

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

- [[Service Level Objective]]
- [[Error Budget]]
- [[Monitoring]]
- [[Incident Response]]

## Nối mạnh

- [[System Reliability]] vì node này thường được kiểm tra cùng khi ra quyết định

## Liên quan rộng

- Production reliability
- Incident management
- Monitoring
- Release governance

## Keywords / Từ khóa tìm kiếm

- Reliability
- độ tin cậy
- release pipeline
- operational readiness
- incident response
- triển khai phần mềm
- vận hành hệ thống
- Service Level Objective
- Error Budget
- Monitoring

## Source trace

- Data Intensive Applications Map / Ch01
- SRE Map
- SEBoK Map / Part 6
