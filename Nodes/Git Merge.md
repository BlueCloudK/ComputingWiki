# Git Merge

Aliases: Git Merge, merge commit

Type: Frameworks and Tools

## Context / Ngữ cảnh

Git Merge xuất hiện khi cần kết hợp lịch sử từ một branch khác vào branch hiện tại mà vẫn giữ quan hệ parent giữa các dòng phát triển.

## Boundary / Ranh giới

### Nó là gì

Git Merge là thao tác tích hợp commit từ branch khác vào branch hiện tại. Nếu lịch sử không fast-forward được, Git tạo merge commit có nhiều parent.

### Nó không phải là gì

Git Merge không giống rebase. Merge giữ cấu trúc lịch sử phân nhánh; rebase viết lại commit lên base mới để lịch sử tuyến tính hơn.

## Core Mechanism / Cơ chế lõi

Git tìm merge base giữa hai branch, tính thay đổi từ mỗi phía, áp dụng chúng vào working tree/index. Nếu cùng vùng file bị sửa khác nhau, Git yêu cầu resolve conflict trước khi tạo merge commit.

## Project Role / Vai trò trong dự án

Dùng node này khi debug conflict, hiểu lịch sử branch, chọn merge strategy cho PR hoặc xử lý integration giữa feature branch và main.

## Output / Artifact nên có

- Merge target/source branch
- Conflict resolution note
- Merge commit nếu có
- Test sau merge
- PR/release context

## Decision Checklist / Câu hỏi kiểm tra

- Merge từ branch nào vào branch nào?
- Có fast-forward được không?
- Conflict được resolve đúng theo intent hai phía chưa?
- Test/build sau merge có pass không?
- Lịch sử merge có phù hợp workflow repo không?

## Failure Modes / Cách nó gây lỗi

- Resolve conflict bằng cách giữ một phía và mất logic phía kia.
- Merge branch sai target.
- Merge commit lớn làm khó hiểu lịch sử.
- Không chạy test sau merge.
- Merge nhiều lần với branch stale gây conflict lặp lại.

## Khi nào chưa cần hoặc dễ over-engineer

- Branch cá nhân ngắn có thể rebase hoặc fast-forward tùy workflow.
- Không nên dùng merge strategy chỉ vì quen tay nếu repo yêu cầu squash/rebase.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Git]] vì merge là thao tác lõi của Git history.
- [[Git Commit]] vì merge có thể tạo merge commit.
- [[Pull Request]] vì PR thường được merge vào main.
- [[Git Remote]] vì merge thường xảy ra sau fetch/pull từ remote branch.

## Liên quan rộng

- Branch history
- Conflict resolution
- Integration workflow

## Keywords / Từ khóa tìm kiếm

- Git Merge
- git merge
- merge commit
- merge conflict
- merge base
- fast-forward merge
- Git merge debugging

## Source trace

- Git documentation
