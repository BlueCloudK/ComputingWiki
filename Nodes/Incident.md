# Incident

Aliases: production issue, sự cố

Type: Reliability / SRE

## Context / Ngữ cảnh

Incident xuất hiện khi production hoặc môi trường quan trọng có lỗi gây user impact, mất dữ liệu, downtime, security risk, cost spike hoặc vận hành bị gián đoạn. Incident không chỉ là bug; nó là tình huống cần phản ứng có tổ chức để giảm impact và học để tránh lặp lại.

## Boundary / Ranh giới

### Nó là gì

Incident là sự cố runtime có impact đủ lớn để cần triage, owner, communication, mitigation và follow-up. Incident thường có timeline, severity, commander/owner, action log, mitigation, resolution và postmortem/action items.

### Nó không phải là gì

Incident không phải mọi error log hoặc bug nhỏ. Nếu không có impact/risk đáng kể và không cần phản ứng khẩn, có thể chỉ là ticket/bug. Incident cũng không kết thúc khi service “xanh” lại; phần học và action item sau đó mới giảm recurrence.

## Core Mechanism / Cơ chế lõi

Incident thường bắt đầu từ alert, user report hoặc operator phát hiện. Team xác định severity, mở channel, phân vai, giảm impact trước, tìm root/cause đủ dùng để mitigate, monitor recovery, communicate status, rồi làm postmortem để tạo action item kỹ thuật/quy trình.

## Project Role / Vai trò trong dự án

Incident giúp team vận hành production mà không loạn khi sự cố xảy ra. Nó buộc team phân biệt detect, respond, mitigate, resolve và learn. Với hệ thống nhiều service, incident process giúp tránh mọi người cùng sửa bừa hoặc thiếu communication với stakeholder.

## Output / Artifact nên có

- Incident record: severity, owner, timeline, affected service/user, current status
- Communication channel và update cadence
- Mitigation/rollback/action log
- Postmortem: impact, contributing factors, what went well/wrong, action items
- Follow-up tracking cho action item giảm recurrence

## Decision Checklist / Câu hỏi kiểm tra

- Impact là gì: user, data, revenue, security, cost hay internal ops?
- Severity/priority hiện tại là bao nhiêu và ai là owner?
- Mitigation nhanh nhất để giảm impact là gì?
- Có cần rollback, disable feature, shed load hoặc block traffic không?
- Ai cần được thông báo và update theo nhịp nào?
- Khi nào coi incident đã resolved?
- Action item nào ngăn lỗi lặp lại?

## Failure Modes / Cách nó gây lỗi

- Không phân owner nên nhiều người nói nhưng không ai quyết.
- Tập trung root cause quá sớm thay vì giảm impact trước.
- Không ghi timeline/action log nên postmortem mơ hồ.
- Communication thiếu làm stakeholder/user không biết trạng thái.
- Resolve khi triệu chứng giảm nhưng guardrail chưa có, lỗi quay lại.
- Postmortem đổ lỗi cá nhân thay vì cải thiện system/process.
- Action item không owner/deadline nên không bao giờ được làm.

## Khi nào chưa cần hoặc dễ over-engineer

- Project cá nhân nhỏ có thể ghi incident note ngắn thay vì process nặng.
- Không nên mở incident cho mọi lỗi nhỏ nếu sẽ làm team mệt và giảm tín hiệu.
- Không nên bỏ qua incident process với dữ liệu/security/payment dù traffic nhỏ.

## Gồm những gì

- [[Incident Response]]
- [[Postmortem]]
- [[Rollback]]

## Nối mạnh

- [[Alert]] vì alert thường là điểm phát hiện incident.
- [[Monitoring]] vì monitoring cung cấp tín hiệu và dashboard trong incident.
- [[Rollback]] vì rollback là mitigation phổ biến khi deploy gây lỗi.
- [[Postmortem]] vì incident cần learning loop sau khi resolve.
- [[Service Level Objective]] vì SLO breach giúp xác định user impact và severity.

## Liên quan rộng

- Production reliability
- Incident management
- Communication
- Learning loop

## Keywords / Từ khóa tìm kiếm

- Incident
- production issue
- sự cố
- incident response
- incident commander
- severity
- mitigation
- resolution
- action log
- incident timeline
- postmortem
- rollback
- user impact
- incident management
- production incident

## Source trace

- Google SRE Book
- SRE Workbook incident response chapters
