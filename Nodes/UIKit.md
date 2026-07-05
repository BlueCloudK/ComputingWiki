# UIKit

Aliases: UIKit

Type: Mobile Development

## Context / Ngữ cảnh

UIKit xuất hiện khi iOS app cần xây giao diện native bằng view controller, view, navigation và event handling của Apple platform.

## Boundary / Ranh giới

### Nó là gì

UIKit là UI framework native của Apple cho iOS/iPadOS, cung cấp view, control, navigation, layout và lifecycle cho app giao diện truyền thống.

### Nó không phải là gì

UIKit không phải Swift và không phải toàn bộ iOS SDK. Swift là ngôn ngữ, UIKit là framework UI.

## Core Mechanism / Cơ chế lõi

App dùng view controller quản lý view hierarchy, lifecycle, layout constraint, navigation và user interaction. UI update cần khớp main thread và lifecycle.

## Project Role / Vai trò trong dự án

Dùng node này khi debug iOS UI, navigation, lifecycle, layout, screen transition hoặc native module dùng UIKit.

## Output / Artifact nên có

- View controller/screen map
- Navigation flow
- Layout constraint note
- Lifecycle handling note
- UI test hoặc manual test checklist

## Decision Checklist / Câu hỏi kiểm tra

- Screen này thuộc view controller nào?
- Navigation flow có rõ không?
- Layout có đúng trên nhiều device không?
- UI update có đúng lifecycle không?

## Failure Modes / Cách nó gây lỗi

- Layout constraint conflict.
- Navigation stack sai.
- Lifecycle xử lý sai làm UI state mất.
- UI update sai thời điểm làm hành vi khó debug.

## Khi nào chưa cần hoặc dễ over-engineer

- App không target iOS native thì chưa cần UIKit.
- Nếu dùng framework UI khác, chỉ cần UIKit ở integration boundary.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[iOS]] vì UIKit là UI framework native của iOS.
- [[Swift]] vì UIKit thường được dùng với Swift.
- [[Xcode]] vì UIKit app thường được build/debug trong Xcode.

## Liên quan rộng

- Native UI
- View controller
- iOS lifecycle

## Keywords / Từ khóa tìm kiếm

- UIKit
- iOS UI
- ViewController
- Auto Layout
- navigation controller
- UIKit debugging

## Source trace

- Apple Developer documentation
