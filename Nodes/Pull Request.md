# Pull Request

Aliases: Pull Request, PR

Type: Frameworks and Tools

## Context / Ngữ cảnh

Pull Request xuất hiện khi code cần được review, kiểm tra tự động và thảo luận trước khi merge vào branch chính.

## Boundary / Ranh giới

### Nó là gì

Pull Request là đơn vị review change trong Git hosting platform. Nó gom diff, commit, discussion, CI status và approval signal.

### Nó không phải là gì

Pull Request không tự đảm bảo chất lượng. Nếu diff quá lớn, test yếu hoặc reviewer không có context, PR chỉ là hình thức.

## Core Mechanism / Cơ chế lõi

Developer push branch, mở PR, CI chạy check, reviewer xem diff và comment. Khi check và approval đạt rule, PR được merge bằng merge commit, squash hoặc rebase tùy workflow.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế workflow review, debug CI check, chia nhỏ change hoặc quản lý release branch.

## Output / Artifact nên có

- PR title/description rõ
- Diff đủ nhỏ để review
- CI status
- Reviewer/owner
- Merge strategy

## Decision Checklist / Câu hỏi kiểm tra

- PR giải quyết issue/change nào?
- Diff có nhỏ và tập trung không?
- Test/check nào phải xanh?
- Reviewer có đủ context không?
- Merge strategy có phù hợp lịch sử repo không?

## Failure Modes / Cách nó gây lỗi

- PR quá lớn làm review hình thức.
- CI thiếu check nên lỗi vào main.
- Description mơ hồ làm reviewer đoán ý.
- Merge conflict xử lý vội làm mất thay đổi.
- Approval không đúng owner domain.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo cá nhân thử nghiệm nhỏ có thể commit trực tiếp.
- Không nên tạo rule review quá nặng nếu team chưa có nhu cầu.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Git]] vì PR dựa trên branch/commit/diff của Git.
- [[CI]] vì PR thường gắn với automated checks.
- [[GitHub Actions]] vì Actions thường chạy check cho PR.
- [[Regression Test]] vì PR nên chạy regression guard trước merge.

## Liên quan rộng

- Code review
- Collaboration workflow
- Branch protection

## Keywords / Từ khóa tìm kiếm

- Pull Request
- PR
- code review
- merge request
- branch protection
- PR checklist
- PR debugging

## Source trace

- GitHub documentation
- Git documentation
