# Dependency Update Bot

Aliases: Dependency Update Bot, dependency bot

Type: Frameworks and Tools

## Context / Ngữ cảnh

Dependency Update Bot xuất hiện khi project cần tự động phát hiện package dependency lỗi thời, tạo pull request update và giúp team giữ dependency không bị tụt quá xa.

## Boundary / Ranh giới

### Nó là gì

Dependency Update Bot là automation đọc manifest/lockfile, kiểm tra version mới, rồi tạo PR hoặc alert để update dependency theo rule.

### Nó không phải là gì

Dependency Update Bot không tự đảm bảo update an toàn. PR update vẫn cần test, review, changelog/risk check và rollback path nếu production bị ảnh hưởng.

## Core Mechanism / Cơ chế lõi

Bot quét dependency file, so với registry/advisory/version policy, tạo branch/PR với manifest và lockfile mới. CI chạy test; reviewer quyết định merge, group, ignore hoặc pin version.

## Project Role / Vai trò trong dự án

Dùng node này khi quản lý dependency drift, security update, lockfile maintenance, monorepo package update hoặc giảm toil update thủ công.

## Output / Artifact nên có

- Bot config
- Update schedule
- Grouping/ignore rule
- PR review checklist
- CI test gate

## Decision Checklist / Câu hỏi kiểm tra

- Bot update dependency nào và tần suất bao nhiêu?
- Major/minor/patch có policy khác nhau không?
- PR có chạy đủ test không?
- Changelog/breaking change có được đọc không?
- Có rule group hoặc limit PR noise không?

## Failure Modes / Cách nó gây lỗi

- Quá nhiều PR làm team bỏ qua.
- Update major merge khi chưa review breaking change.
- Lockfile update sai package manager.
- CI test yếu nên regression lọt qua.
- Ignore rule rộng làm dependency lỗi thời mãi.

## Khi nào chưa cần hoặc dễ over-engineer

- Repo thử nghiệm nhỏ có thể update thủ công trước.
- Không nên bật update ồ ạt nếu CI/test chưa đủ tin.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dependency Resolver]] vì bot thay đổi dependency graph/lockfile.
- [[Pull Request]] vì bot thường tạo PR update.
- [[CI]] vì update cần test gate.
- [[Package Registry]] vì version mới lấy từ registry/advisory.

## Liên quan rộng

- Dependency maintenance
- Security patching
- Automation PR

## Keywords / Từ khóa tìm kiếm

- Dependency Update Bot
- dependency bot
- Dependabot
- Renovate
- dependency update PR
- lockfile update
- dependency bot debugging

## Source trace

- GitHub Dependabot documentation
- Renovate documentation
