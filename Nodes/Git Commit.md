# Git Commit

Aliases: Git Commit, commit

Type: Frameworks and Tools

## Context / Ngữ cảnh

Git Commit xuất hiện khi cần lưu một snapshot thay đổi trong Git history để review, rollback, trace bug hoặc làm mốc cho build/release.

## Boundary / Ranh giới

### Nó là gì

Git Commit là object trong Git ghi lại tree snapshot, metadata, author/committer, message và parent commit để tạo lịch sử thay đổi.

### Nó không phải là gì

Git Commit không phải file diff tạm thời trong working tree. Commit là mốc lịch sử đã được ghi vào repository local và có thể push lên remote.

## Core Mechanism / Cơ chế lõi

Developer stage file vào index, tạo commit từ index, Git lưu snapshot và parent pointer. Branch chỉ trỏ tới commit mới nhất trong một dòng lịch sử.

## Project Role / Vai trò trong dự án

Dùng node này khi debug lịch sử Git, chia nhỏ change, trace bug về commit, viết commit message rõ hoặc hiểu CI/release artifact gắn với SHA nào.

## Output / Artifact nên có

- Commit SHA
- Commit message rõ intent
- Diff đủ nhỏ và tập trung
- Parent/history context
- Link tới PR/issue nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Commit này giải quyết một ý rõ chưa?
- Diff có lẫn format/refactor/logic không?
- Message có nói vì sao thay đổi không?
- Commit có build/test pass không?
- Commit SHA có được dùng để trace artifact không?

## Failure Modes / Cách nó gây lỗi

- Commit quá lớn làm review và rollback khó.
- Message mơ hồ làm lịch sử vô dụng.
- Commit chứa secret hoặc file build rác.
- Commit chưa test nhưng đã push/merge.
- Squash/rebase làm mất context nếu không giữ message tốt.

## Khi nào chưa cần hoặc dễ over-engineer

- Thử nghiệm local nhanh có thể commit tạm, nhưng trước khi share nên dọn lịch sử hợp lý.
- Không nên chia commit quá nhỏ nếu mỗi commit không build/test được.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Git]] vì commit là object lõi của Git.
- [[Pull Request]] vì PR gom commit/diff để review.
- [[Git Remote]] vì commit cần push/fetch qua remote để collaboration.
- [[Release Artifact]] vì artifact nên trace được về commit SHA.

## Liên quan rộng

- Version history
- Code review
- Traceability

## Keywords / Từ khóa tìm kiếm

- Git Commit
- commit SHA
- commit message
- git commit
- staged changes
- parent commit
- commit debugging

## Source trace

- Git documentation
