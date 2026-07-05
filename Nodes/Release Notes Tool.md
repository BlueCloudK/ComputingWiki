# Release Notes Tool

Aliases: Release Notes Tool, release note generator

Type: Frameworks and Tools

## Context / Ngữ cảnh

Release Notes Tool xuất hiện khi project cần tạo release note/changelog từ pull request, commit, issue, tag hoặc label một cách lặp lại và ít thủ công.

## Boundary / Ranh giới

### Nó là gì

Release Notes Tool là tool tự động gom và format thay đổi của một release thành note cho user, stakeholder hoặc developer.

### Nó không phải là gì

Release Notes Tool không tự làm nội dung hữu ích nếu PR title, label, changelog convention hoặc breaking change note bị viết kém.

## Core Mechanism / Cơ chế lõi

Tool đọc range giữa các tag hoặc milestone, lấy PR/commit/issue metadata, nhóm theo label/type, rồi sinh markdown hoặc GitHub release note theo template.

## Project Role / Vai trò trong dự án

Dùng node này khi chuẩn hóa release note, giảm toil release, trace breaking change hoặc public changelog cho repo/sản phẩm.

## Output / Artifact nên có

- Release note template
- Tag/version range
- Grouping label/type rule
- Breaking change section
- Publish target: file, GitHub Release, docs

## Decision Checklist / Câu hỏi kiểm tra

- Release note phục vụ user hay developer?
- Source là PR, commit hay issue?
- Tag range có đúng không?
- Breaking change có nổi bật không?
- Note có link về PR/issue khi cần không?

## Failure Modes / Cách nó gây lỗi

- Tag range sai làm thiếu hoặc lặp change.
- PR title mơ hồ khiến note vô dụng.
- Breaking change bị chôn trong list dài.
- Tool publish nhầm draft/release.
- Automation đẹp nhưng không ai kiểm lại nội dung cuối.

## Khi nào chưa cần hoặc dễ over-engineer

- Project chưa release định kỳ có thể viết release note thủ công.
- Không nên dùng tool phức tạp nếu PR/label convention chưa ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Changelog Generation]] vì release notes tool thực thi việc sinh changelog/release note.
- [[Release Artifact]] vì release note nên gắn với artifact/version.
- [[Pull Request]] vì PR metadata thường là nguồn note tốt.
- [[Git]] vì tag/commit range là input chính.

## Liên quan rộng

- Release note
- Changelog automation
- Versioning

## Keywords / Từ khóa tìm kiếm

- Release Notes Tool
- release note generator
- changelog generator
- GitHub release notes
- tag range
- release note automation
- release notes debugging

## Source trace

- GitHub Releases documentation
- Git documentation
