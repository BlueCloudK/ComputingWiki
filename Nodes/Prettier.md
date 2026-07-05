# Prettier

Aliases: Prettier

Type: Frameworks and Tools

## Context / Ngữ cảnh

Prettier xuất hiện khi JavaScript/TypeScript/CSS/Markdown project cần format code tự động và thống nhất giữa developer, editor và CI.

## Boundary / Ranh giới

### Nó là gì

Prettier là opinionated code formatter. Nó parse source file rồi in lại theo style rule cố định để giảm tranh luận thủ công về formatting.

### Nó không phải là gì

Prettier không phải linter logic. Nó không thay thế ESLint, type checker, test hoặc review kiến trúc.

## Core Mechanism / Cơ chế lõi

Prettier đọc file, tạo AST nếu hỗ trợ, rồi rewrite whitespace, line break, quote, trailing comma và format bề mặt theo config/version. Output nên deterministic.

## Project Role / Vai trò trong dự án

Dùng node này khi setup formatting, debug CI format fail, giảm diff nhiễu trong pull request hoặc chuẩn hóa style repo public.

## Output / Artifact nên có

- Prettier config
- Ignore file
- Format command
- CI format check
- Editor integration note

## Decision Checklist / Câu hỏi kiểm tra

- Prettier version có pin không?
- File/generated folder nào cần ignore?
- Editor format có khớp CI không?
- Format chạy auto-fix local hay check-only CI?
- Prettier có conflict với linter rule không?

## Failure Modes / Cách nó gây lỗi

- Local và CI dùng Prettier version khác.
- Format trên generated/vendor file làm diff lớn.
- Prettier và ESLint tranh cùng một rule.
- PR chứa cả logic change và format toàn repo.
- Không có script chung nên mỗi người chạy khác nhau.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo nhỏ một người có thể dùng config mặc định đơn giản.
- Không nên tranh luận style thủ công nếu formatter đã được chọn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Formatter]] vì Prettier là một formatter cụ thể.
- [[Pull Request]] vì format ổn giúp diff dễ review hơn.
- [[CI]] vì format check thường chạy trong pipeline.
- [[JavaScript]] vì Prettier phổ biến trong JavaScript ecosystem.

## Liên quan rộng

- Code style
- Developer workflow
- Editor tooling

## Keywords / Từ khóa tìm kiếm

- Prettier
- code formatter
- prettier config
- format check
- prettier ignore
- prettier debugging

## Source trace

- Prettier documentation
