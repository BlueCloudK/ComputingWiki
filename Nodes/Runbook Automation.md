# Runbook Automation

Aliases: Runbook Automation, automated runbook

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Runbook Automation xuất hiện khi thao tác vận hành lặp lại như restart service, scale resource, collect diagnostics, rollback hoặc cleanup có thể được chuẩn hóa và chạy bán/tự động.

## Boundary / Ranh giới

### Nó là gì

Runbook Automation là việc biến runbook thủ công thành workflow/script/job có input, guardrail, approval, logging và rollback/stop condition rõ.

### Nó không phải là gì

Runbook Automation không phải chạy script tùy tiện trên production. Automation vận hành cần idempotency, permission nhỏ, audit log và human override nếu có risk.

## Core Mechanism / Cơ chế lõi

Runbook mô tả step xử lý. Automation nhận trigger hoặc operator input, kiểm tra điều kiện, chạy action theo thứ tự, ghi log/result và dừng nếu guardrail fail.

## Project Role / Vai trò trong dự án

Dùng node này khi giảm toil SRE/devops, chuẩn hóa incident response, tự động hóa rollback/diagnostics hoặc tạo action an toàn cho on-call.

## Output / Artifact nên có

- Automated runbook workflow
- Input/output schema
- Guardrail and approval rule
- Audit log
- Rollback/stop condition

## Decision Checklist / Câu hỏi kiểm tra

- Step nào đủ an toàn để tự động hóa?
- Automation có idempotent không?
- Cần approval trước action nào?
- Log có đủ để audit/debug không?
- Nếu action fail giữa chừng thì dừng hay rollback?

## Failure Modes / Cách nó gây lỗi

- Automation chạy sai environment.
- Script không idempotent làm lỗi lặp nặng hơn.
- Permission quá rộng gây blast radius lớn.
- Không có dry-run/approval cho action nguy hiểm.
- Log thiếu khiến không biết automation đã làm gì.

## Khi nào chưa cần hoặc dễ over-engineer

- Incident hiếm và chưa hiểu manual process thì chưa nên tự động hóa ngay.
- Không nên automate trước khi runbook thủ công đã đủ rõ và an toàn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Incident Response]] vì runbook automation thường dùng trong incident.
- [[Rollback]] vì rollback có thể được chuẩn hóa thành runbook.
- [[Least Privilege]] vì automation nên có quyền tối thiểu.
- [[Logging]] vì audit log là yêu cầu quan trọng.

## Liên quan rộng

- Toil reduction
- SRE automation
- Operational workflow

## Keywords / Từ khóa tìm kiếm

- Runbook Automation
- automated runbook
- incident automation
- operational script
- dry run
- runbook workflow
- runbook automation debugging

## Source trace

- Google SRE Books
- Kubernetes official docs
