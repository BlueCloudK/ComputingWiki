# Git Remote

Aliases: Git Remote, remote repository

Type: Frameworks and Tools

## Context / Ngữ cảnh

Git Remote xuất hiện khi local repository cần đồng bộ code với repository ở máy chủ như GitHub, GitLab hoặc server nội bộ.

## Boundary / Ranh giới

### Nó là gì

Git Remote là tên trỏ tới repository bên ngoài local machine. Remote thường có URL, tên như `origin`, và branch tracking để push/pull/fetch.

### Nó không phải là gì

Git Remote không phải branch. Remote là nơi chứa repo; branch là dòng lịch sử trong repo.

## Core Mechanism / Cơ chế lõi

Git lưu remote URL trong config. `fetch` lấy ref mới về local, `pull` lấy và merge/rebase, `push` gửi commit local lên remote branch.

## Project Role / Vai trò trong dự án

Dùng node này khi debug push/pull fail, sai origin, sai branch tracking, permission hoặc đồng bộ fork/upstream.

## Output / Artifact nên có

- Remote list
- Remote URL
- Branch tracking note
- Auth/permission note
- Fork/upstream convention nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Remote nào là source of truth?
- URL dùng HTTPS hay SSH?
- Branch local đang track remote branch nào?
- Push/pull có đúng remote không?
- Fork và upstream có tách rõ không?

## Failure Modes / Cách nó gây lỗi

- Push nhầm remote hoặc branch.
- Local track sai upstream branch.
- Remote URL dùng credential sai.
- Fetch chưa cập nhật nên nhìn lịch sử cũ.
- Fork/upstream lẫn lộn làm PR sai target.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo local thử nghiệm chưa cần remote.
- Không nên thêm nhiều remote nếu team không có workflow fork/upstream rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Git]] vì remote là phần của Git workflow.
- [[Pull Request]] vì PR thường đi từ branch trên remote.
- [[CI]] vì push lên remote thường trigger CI.

## Liên quan rộng

- Version control
- Repository hosting
- Collaboration workflow

## Keywords / Từ khóa tìm kiếm

- Git Remote
- git remote
- origin
- upstream
- git fetch
- git pull
- git push
- remote tracking branch
- Git remote debugging

## Source trace

- Git documentation
