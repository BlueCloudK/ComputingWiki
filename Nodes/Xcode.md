# Xcode

Aliases: Xcode

Type: Mobile Development

## Context / Ngữ cảnh

Xcode xuất hiện khi phát triển app cho iOS, macOS hoặc hệ sinh thái Apple, từ viết code, build, debug đến archive và release.

## Boundary / Ranh giới

### Nó là gì

Xcode là IDE và toolchain chính của Apple để viết, build, ký, chạy test, debug và phát hành app.

### Nó không phải là gì

Xcode không phải ngôn ngữ lập trình. Swift hoặc Objective-C mới là ngôn ngữ thường dùng trong project Apple.

## Core Mechanism / Cơ chế lõi

Xcode quản lý project/workspace, target, scheme, signing, simulator/device run, build setting, asset, test và archive release.

## Project Role / Vai trò trong dự án

Dùng node này khi debug iOS build, signing, simulator/device, archive, test hoặc release app.

## Output / Artifact nên có

- Xcode project/workspace
- Scheme/target note
- Signing config
- Archive/release artifact
- Simulator/device test note

## Decision Checklist / Câu hỏi kiểm tra

- Target/scheme có đúng không?
- Signing team/profile đúng chưa?
- Build setting có lệch debug/release không?
- Simulator/device target là gì?
- Archive/export có dùng đúng method không?

## Failure Modes / Cách nó gây lỗi

- Signing sai làm app không chạy hoặc không upload được.
- Scheme/target sai làm build nhầm app.
- Debug/release config lệch.
- Simulator pass nhưng device fail.
- Xcode/SDK version khác CI làm build lệch.

## Khi nào chưa cần hoặc dễ over-engineer

- Không target Apple platform thì chưa cần Xcode.
- Không nên phụ thuộc config local nếu CI/release cần reproducible build.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[iOS]] vì Xcode là toolchain chính để phát triển iOS app.
- [[Swift]] vì Swift thường được viết và build trong Xcode.
- [[SDK]] vì Xcode đi kèm Apple SDK.
- [[IPA]] vì Xcode archive/export có thể tạo IPA.

## Liên quan rộng

- Apple development
- App signing
- Simulator
- Release archive

## Keywords / Từ khóa tìm kiếm

- Xcode
- Xcode project
- Xcode scheme
- iOS signing
- simulator
- archive
- Xcode debugging

## Source trace

- Apple Developer documentation
