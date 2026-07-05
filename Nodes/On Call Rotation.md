# On Call Rotation

Aliases: On Call Rotation, on-call rotation

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

On Call Rotation xuất hiện khi service production cần người chịu trách nhiệm nhận alert, triage incident và xử lý sự cố ngoài giờ hoặc theo ca trực.

## Boundary / Ranh giới

### Nó là gì

On Call Rotation là lịch phân công người/nhóm trực vận hành, kèm escalation, handoff, ownership và runbook để phản hồi incident.

### Nó không phải là gì

On Call Rotation không tự làm hệ thống đáng tin hơn. Nếu alert nhiễu, runbook kém hoặc escalation mơ hồ, người trực chỉ bị overload.

## Core Mechanism / Cơ chế lõi

Rotation định nghĩa primary/secondary on-call theo khung giờ. Alert route tới người trực, người trực acknowledge, triage, escalate nếu cần và ghi lại action/postmortem cho incident đáng kể.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế incident response, alert routing, ownership service, handoff ca trực hoặc giảm burnout/noise trong vận hành production.

## Output / Artifact nên có

- Rotation schedule
- Primary/secondary owner
- Escalation policy
- Runbook link
- Handoff and post-incident note

## Decision Checklist / Câu hỏi kiểm tra

- Ai là primary và secondary?
- Alert nào page người trực, alert nào chỉ ticket/log?
- Escalation sau bao lâu?
- Runbook có đủ để xử lý lúc nửa đêm không?
- Rotation có công bằng và tránh burnout không?

## Failure Modes / Cách nó gây lỗi

- Alert quá nhiễu làm người trực bỏ qua.
- Không có secondary/escalation nên incident kẹt.
- Handoff thiếu context làm lỗi kéo dài.
- Service owner không rõ nên ai cũng tưởng người khác xử lý.
- Runbook stale khiến người trực làm sai bước.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không có production user hoặc SLA thấp có thể chưa cần on-call formal.
- Không nên bật paging 24/7 nếu alert chưa chất lượng và runbook chưa có.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Incident Response]] vì on-call là người thực thi incident response đầu tiên.
- [[Alert]] vì alert route tới on-call.
- [[Escalation Policy]] vì rotation cần escalation khi primary không xử lý được.
- [[Runbook Automation]] vì runbook tốt giảm toil cho người trực.

## Liên quan rộng

- SRE operations
- Alert routing
- Incident ownership

## Keywords / Từ khóa tìm kiếm

- On Call Rotation
- on-call rotation
- incident on-call
- primary secondary on-call
- alert routing
- handoff
- on-call rotation debugging

## Source trace

- Google SRE Books
- Incident management documentation
