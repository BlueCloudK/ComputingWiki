# Workflow Dispatch

Aliases: Workflow Dispatch, manual workflow trigger

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Workflow Dispatch xuất hiện khi CI/CD workflow cần được chạy thủ công với input cụ thể, thay vì chỉ trigger từ push, pull request hoặc schedule.

## Boundary / Ranh giới

### Nó là gì

Workflow Dispatch là cơ chế trigger thủ công workflow, thường trong GitHub Actions, cho phép operator chọn branch/ref và truyền input như environment, version hoặc action.

### Nó không phải là gì

Workflow Dispatch không phải nút bấm an toàn mặc định. Nếu input/permission/approval yếu, nó có thể chạy deploy, rollback hoặc job nhạy cảm sai môi trường.

## Core Mechanism / Cơ chế lõi

Workflow định nghĩa trigger `workflow_dispatch` và input schema. Người có quyền chạy chọn ref/input; GitHub Actions tạo run và job đọc input để quyết định bước tiếp theo.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế manual deploy, hotfix, rollback, maintenance job, data migration hoặc debug pipeline cần operator-controlled action.

## Output / Artifact nên có

- Workflow dispatch input schema
- Permission rule
- Environment/approval gate
- Audit log/run link
- Rollback or dry-run option nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Ai được quyền dispatch workflow?
- Input có enum/validation rõ không?
- Workflow chạy trên branch/ref nào?
- Job nhạy cảm có environment approval không?
- Run có log/audit đủ để trace không?

## Failure Modes / Cách nó gây lỗi

- Operator chọn nhầm environment.
- Input tự do làm script chạy lệnh sai.
- Workflow chạy từ branch không mong muốn.
- Secret được expose cho run không cần thiết.
- Manual trigger bypass test/approval bình thường.

## Khi nào chưa cần hoặc dễ over-engineer

- Job tự động đơn giản có thể dùng push/schedule trigger.
- Không nên dùng workflow dispatch để thay thế release process có gate rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[GitHub Actions]] vì workflow dispatch là trigger phổ biến trong Actions.
- [[Deployment Approval]] vì manual deploy thường cần approval gate.
- [[Pipeline Secret]] vì workflow run có thể dùng secret nhạy cảm.
- [[Rollback]] vì rollback thủ công thường chạy qua workflow dispatch.

## Liên quan rộng

- Manual CI trigger
- Operator action
- Release operations

## Keywords / Từ khóa tìm kiếm

- Workflow Dispatch
- manual workflow trigger
- GitHub Actions workflow_dispatch
- workflow input
- manual deploy
- workflow dispatch debugging

## Source trace

- GitHub Actions documentation
