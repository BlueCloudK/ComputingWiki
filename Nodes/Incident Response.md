# Incident Response

Aliases: incident response, ứng phó sự cố

Type: Reliability / SRE

## Context / Ngữ cảnh

Incident Response xuất hiện khi production có sự cố và team cần phản ứng nhanh, có tổ chức để giảm user impact, bảo vệ dữ liệu, phục hồi service và giao tiếp rõ với stakeholder. Nó thường bắt đầu từ alert, user report, security signal hoặc monitoring anomaly.

## Boundary / Ranh giới

### Nó là gì

Incident Response là quy trình xử lý sự cố trong lúc đang xảy ra: triage, phân severity, chỉ định owner/commander, mở kênh liên lạc, giảm impact, rollback/mitigate, theo dõi recovery và cập nhật trạng thái. Mục tiêu đầu tiên là giảm thiệt hại, không phải tìm root cause hoàn hảo ngay lập tức.

### Nó không phải là gì

Incident Response không phải postmortem. Postmortem diễn ra sau khi sự cố đã ổn định để học và tạo action item. Incident Response cũng không phải debugging cá nhân tự phát; nếu nhiều người cùng sửa nhưng không có owner/timeline/communication, incident dễ loạn và kéo dài.

## Core Mechanism / Cơ chế lõi

Khi tín hiệu sự cố xuất hiện, team xác nhận impact, phân severity, chỉ định người điều phối, lập timeline/action log, giảm impact bằng rollback, disable feature, scale, shed load hoặc block traffic, rồi monitor cho tới khi service ổn định. Sau đó chuyển sang postmortem và follow-up.

## Project Role / Vai trò trong dự án

Incident Response giúp team vận hành production có kỷ luật. Nó làm rõ ai quyết định, ai giao tiếp, ai debug, ai rollback và khi nào cần escalate. Với hệ thống nhiều service, quy trình này tránh việc mọi người sửa ngẫu nhiên và làm blast radius lớn hơn.

## Output / Artifact nên có

- Incident response checklist: detect, declare, assign owner, communicate, mitigate, resolve
- Severity rubric: SEV1/SEV2/SEV3 hoặc mức tương đương
- Communication template: impact, scope, ETA update, owner, next update
- Action log/timeline trong lúc xử lý
- Handoff sang postmortem với dữ liệu, timeline và action items ban đầu

## Decision Checklist / Câu hỏi kiểm tra

- Impact hiện tại là gì: downtime, latency, data, security, cost hay internal ops?
- Severity là bao nhiêu và ai là incident owner/commander?
- Mitigation nhanh nhất để giảm impact là gì?
- Có cần rollback, disable feature, scale, shed load hoặc block traffic không?
- Ai cần được thông báo và update theo cadence nào?
- Metric nào chứng minh sự cố đã ổn định?
- Sau khi ổn định, dữ liệu nào cần giữ cho postmortem?

## Failure Modes / Cách nó gây lỗi

- Không declare incident nên mọi người xử lý rời rạc và thiếu owner.
- Tập trung tìm root cause quá sớm trong khi user impact vẫn tăng.
- Không ghi action log nên không biết thay đổi nào giúp hoặc làm tệ hơn.
- Communication thiếu làm stakeholder/user tưởng team không xử lý.
- Nhiều người cùng thay đổi production làm blast radius lớn hơn.
- Không có criteria resolved nên đóng incident khi triệu chứng chỉ tạm giảm.

## Khi nào chưa cần hoặc dễ over-engineer

- Project cá nhân nhỏ có thể dùng checklist ngắn thay vì quy trình formal.
- Không nên mở incident cho mọi lỗi nhỏ nếu sẽ làm team mệt và giảm tín hiệu.
- Với data/security/payment, vẫn nên có response path rõ dù traffic thấp.

## Gồm những gì

- [[Incident]]
- [[Alert]]
- [[Postmortem]]
- [[Rollback]]

## Nối mạnh

- [[Incident]] vì incident response là phần xử lý active của incident.
- [[Alert]] vì alert thường là tín hiệu mở incident response.
- [[Rollback]] vì rollback là mitigation phổ biến khi deploy gây lỗi.
- [[Monitoring]] vì response cần metric/log để biết impact và recovery.
- [[Postmortem]] vì sau response cần learning loop để giảm recurrence.

## Liên quan rộng

- On-call operations
- Production reliability
- Crisis communication
- Mitigation strategy

## Keywords / Từ khóa tìm kiếm

- Incident Response
- incident response
- ứng phó sự cố
- incident commander
- severity
- mitigation
- action log
- incident timeline
- status update
- rollback mitigation
- incident communication
- production incident response
- on-call response
- incident checklist

## Source trace

- Google SRE Book
- SRE Workbook incident response chapters
