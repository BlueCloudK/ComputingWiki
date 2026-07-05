# Changelog Generation

Aliases: Changelog Generation, changelog automation

Type: Frameworks and Tools

## Context / Ngữ cảnh

Changelog Generation xuất hiện khi project cần tạo danh sách thay đổi cho release từ commit, pull request, tag hoặc issue một cách lặp lại.

## Boundary / Ranh giới

### Nó là gì

Changelog Generation là quá trình tạo changelog từ metadata phát triển như commit message, PR title, label, milestone và release tag.

### Nó không phải là gì

Changelog Generation không tự đảm bảo release note hữu ích. Nếu commit/PR message kém, changelog tự động cũng sẽ nhiễu.

## Core Mechanism / Cơ chế lõi

Tool đọc range commit hoặc PR giữa hai tag, nhóm change theo type/label, tạo markdown/release note và gắn với release artifact hoặc GitHub release.

## Project Role / Vai trò trong dự án

Dùng node này khi chuẩn hóa release note, tự động hóa release, trace breaking change hoặc tạo lịch sử thay đổi cho user/team.

## Output / Artifact nên có

- Changelog file hoặc release note
- Tag/version range
- Grouping rule
- Breaking change section
- Link tới PR/issue nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Changelog lấy nguồn từ commit hay PR?
- Version range bắt đầu/kết thúc ở tag nào?
- Change được nhóm theo rule nào?
- Breaking change có nổi bật không?
- User đọc changelog này là ai?

## Failure Modes / Cách nó gây lỗi

- Commit message mơ hồ làm changelog vô dụng.
- Tag range sai làm thiếu hoặc lặp change.
- Breaking change bị chôn trong danh sách dài.
- Changelog chỉ phục vụ dev, không giúp user hiểu impact.
- Automation publish nhầm draft/release.

## Khi nào chưa cần hoặc dễ over-engineer

- Project chưa có release định kỳ có thể ghi release note thủ công.
- Không nên tự động hóa quá sớm nếu commit/PR convention chưa ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Release Artifact]] vì changelog thường đi cùng artifact/version release.
- [[Pull Request]] vì PR title/label thường là nguồn changelog tốt.
- [[Git]] vì tag/commit range là input chính.
- [[CD]] vì pipeline release có thể tạo changelog tự động.

## Liên quan rộng

- Release note
- Versioning
- Developer workflow

## Keywords / Từ khóa tìm kiếm

- Changelog Generation
- changelog automation
- release notes
- conventional commits
- Git tag range
- changelog debugging

## Source trace

- Git documentation
- GitHub Releases documentation
