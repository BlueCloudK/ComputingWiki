# Postmortem

Aliases: post-incident review, báo cáo sau sự cố

Type: Reliability / SRE

## Context / Ngữ cảnh

Postmortem xuất hiện sau một incident hoặc near miss quan trọng để team hiểu điều gì đã xảy ra, vì sao hệ thống cho phép nó xảy ra, impact là gì và cần thay đổi gì để giảm khả năng lặp lại. Nó là phần learning loop của reliability.

## Boundary / Ranh giới

### Nó là gì

Postmortem là review sau sự cố, thường gồm timeline, impact, contributing factors, detection, response, what went well, what went wrong và action items. Postmortem tốt tập trung vào hệ thống/quy trình, không đổ lỗi cá nhân.

### Nó không phải là gì

Postmortem không phải buổi tìm người chịu tội và cũng không phải báo cáo cho có. Nếu không có action item rõ owner/deadline, postmortem chỉ là tài liệu lưu trữ. Nó cũng không thay thế incident response; response giảm impact trước, postmortem học sau.

## Core Mechanism / Cơ chế lõi

Sau khi incident resolved, team thu timeline từ alert, log, deploy, chat và action log. Sau đó phân tích contributing factors: technical, process, monitoring, testing, rollout, communication. Cuối cùng tạo action items nhỏ, có owner, deadline và cơ chế theo dõi.

## Project Role / Vai trò trong dự án

Postmortem giúp knowledge vault và team tích lũy kinh nghiệm thực tế thay vì lặp lại lỗi. Nó biến incident thành cải tiến cụ thể: alert tốt hơn, rollback nhanh hơn, test mới, migration an toàn hơn, runbook rõ hơn hoặc kiến trúc ít blast radius hơn.

## Output / Artifact nên có

- Incident summary: impact, severity, duration, affected users/services
- Timeline: detection, major actions, mitigation, recovery, resolution
- Contributing factors thay vì chỉ một root cause đơn giản
- What went well / what went wrong / where we got lucky
- Action items: owner, deadline, expected prevention/detection improvement
- Link tới alert, dashboard, logs, commits/deployments liên quan nếu có

## Decision Checklist / Câu hỏi kiểm tra

- User impact thật là gì và kéo dài bao lâu?
- Sự cố được phát hiện bằng alert, user report hay may mắn?
- Mitigation nào giúp giảm impact nhanh nhất?
- Timeline có đủ chính xác để học không?
- Contributing factors nằm ở code, config, deploy, monitoring, process hay communication?
- Action item có owner/deadline và measurable outcome không?
- Có action nào giảm recurrence hoặc giảm time-to-detect/time-to-mitigate không?

## Failure Modes / Cách nó gây lỗi

- Postmortem đổ lỗi cá nhân làm team che giấu lỗi lần sau.
- Timeline thiếu dữ liệu nên phân tích dựa trên cảm giác.
- Chỉ ghi “root cause” đơn giản và bỏ qua contributing factors.
- Action item quá lớn/không owner nên không được làm.
- Không theo dõi action item nên lỗi lặp lại.
- Không chia sẻ bài học nên team khác mắc cùng failure mode.

## Khi nào chưa cần hoặc dễ over-engineer

- Incident nhỏ không user impact có thể cần note ngắn thay vì postmortem formal.
- Không nên làm ceremony nặng nếu action item rõ và scope nhỏ.
- Không nên bỏ postmortem cho sự cố data/security/payment chỉ vì downtime ngắn.

## Gồm những gì

- [[Incident]]
- [[Incident Response]]

## Nối mạnh

- [[Incident]] vì postmortem phân tích incident sau khi resolved.
- [[Incident Response]] vì action log trong response là dữ liệu đầu vào cho postmortem.
- [[Monitoring]] vì postmortem thường cải thiện detection/alert/dashboard.
- [[Alert]] vì nhiều action item là sửa alert quá muộn hoặc quá noisy.
- [[Error Budget]] vì incident tiêu budget và ảnh hưởng release governance.

## Liên quan rộng

- Blameless culture
- Learning loop
- Reliability improvement
- Action item tracking

## Keywords / Từ khóa tìm kiếm

- Postmortem
- post-incident review
- báo cáo sau sự cố
- blameless postmortem
- incident timeline
- contributing factors
- action items
- recurrence prevention
- what went well
- what went wrong
- near miss review
- postmortem template
- incident learning

## Source trace

- Google SRE Book
- SRE Workbook postmortem guidance
