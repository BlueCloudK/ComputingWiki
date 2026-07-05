# Formatter

Aliases: Formatter, code formatter

Type: Frameworks and Tools

## Context / Ngữ cảnh

Formatter xuất hiện khi team cần code style nhất quán để giảm tranh luận thủ công và làm diff dễ review hơn.

## Boundary / Ranh giới

### Nó là gì

Formatter là tool tự động sắp xếp whitespace, indentation, line break và style bề mặt của code theo rule định sẵn.

### Nó không phải là gì

Formatter không phải linter đầy đủ. Formatter chỉnh hình thức; linter thường bắt bug pattern, rule chất lượng hoặc convention logic hơn.

## Core Mechanism / Cơ chế lõi

Tool parse code hoặc text, áp style rule rồi rewrite file. Formatter thường chạy local, pre-commit hoặc CI check để đảm bảo output ổn định.

## Project Role / Vai trò trong dự án

Dùng node này khi setup code style, debug CI format fail, giảm diff nhiễu hoặc chuẩn hóa repo nhiều người làm.

## Output / Artifact nên có

- Formatter config
- Format command
- CI check rule
- Editor integration note
- Exclude/generated file rule

## Decision Checklist / Câu hỏi kiểm tra

- Tool format chính là gì?
- Config có commit vào repo không?
- Local editor có khớp CI không?
- Generated file có exclude không?
- Format chạy check hay auto-fix ở CI?

## Failure Modes / Cách nó gây lỗi

- Local format khác CI.
- Formatter chạy trên generated/vendor file.
- PR toàn diff format che logic change.
- Tool version không pin làm output đổi.
- Formatter và linter rule conflict.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo nhỏ một người có thể dùng config đơn giản.
- Không nên tranh luận style thủ công nếu formatter đã quyết định.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì format check thường chạy trong pipeline.
- [[IDE]] vì editor integration giúp format local khớp repo.
- [[Pull Request]] vì formatter giảm diff nhiễu khi review.

## Liên quan rộng

- Code style
- Developer workflow
- Linting

## Keywords / Từ khóa tìm kiếm

- Formatter
- code formatter
- format check
- Prettier
- Black
- clang-format
- formatter debugging

## Source trace

- Prettier documentation
- Black documentation
