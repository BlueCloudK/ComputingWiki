# iOS

Aliases: iOS

Type: Mobile Development

## Context / Ngữ cảnh

iOS xuất hiện khi app cần chạy trên iPhone/iPad, dùng ecosystem Apple, App Store release, native UI và platform capability riêng.

## Boundary / Ranh giới

### Nó là gì

iOS là mobile operating system của Apple cho iPhone. Với developer, iOS là target platform có SDK, lifecycle, permission, storage, networking, UI framework và release process riêng.

### Nó không phải là gì

iOS không phải Swift hoặc Xcode, dù hai thứ đó thường dùng để phát triển iOS app.

## Core Mechanism / Cơ chế lõi

App iOS được build bằng toolchain Apple, chạy trong sandbox, tương tác với system API qua permission/capability, và được phân phối qua App Store hoặc test channel.

## Project Role / Vai trò trong dự án

Dùng node này khi cần hiểu target platform, app lifecycle, permission, release, device compatibility hoặc native integration cho iOS.

## Output / Artifact nên có

- Platform target note
- Permission/capability list
- App lifecycle note
- Release/test channel decision

## Decision Checklist / Câu hỏi kiểm tra

- App cần capability iOS nào?
- Target version/device là gì?
- Permission có được giải thích rõ không?
- Release qua kênh nào?

## Failure Modes / Cách nó gây lỗi

- Permission thiếu hoặc mô tả sai.
- Device/version không tương thích.
- App lifecycle xử lý sai làm mất state.
- Release config sai làm build không upload được.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không target iOS thì chưa cần đào sâu.

## Gồm những gì

- [[Swift]]
- [[UIKit]]
- [[Xcode]]

## Nối mạnh

- [[Swift]] vì Swift là ngôn ngữ phổ biến cho iOS app.
- [[Xcode]] vì Xcode là IDE/toolchain chính cho iOS.
- [[UIKit]] vì UIKit là UI framework native của iOS.

## Liên quan rộng

- Apple platform
- Mobile app lifecycle
- App Store release

## Keywords / Từ khóa tìm kiếm

- iOS
- iPhone app
- iOS SDK
- iOS permission
- App Store
- iOS debugging

## Source trace

- Apple Developer documentation
