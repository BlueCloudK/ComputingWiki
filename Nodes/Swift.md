# Swift

Aliases: Swift

Type: Mobile Development

## Context / Ngữ cảnh

Swift xuất hiện khi phát triển app trong hệ sinh thái Apple như iOS, macOS, watchOS hoặc tvOS.

## Boundary / Ranh giới

### Nó là gì

Swift là ngôn ngữ lập trình của Apple, dùng nhiều cho app iOS và các platform Apple.

### Nó không phải là gì

Swift không phải iOS và không phải Xcode. iOS là platform, Xcode là toolchain, Swift là ngôn ngữ.

## Core Mechanism / Cơ chế lõi

Swift có static typing, optionals, value type, protocol, async/await và interop với framework Apple. Code được build bằng toolchain Apple để chạy trên target platform.

## Project Role / Vai trò trong dự án

Dùng node này khi debug iOS code, optional crash, concurrency, build setting hoặc native module Apple.

## Output / Artifact nên có

- Swift source/module
- Xcode target/scheme
- Platform target note
- Test cho logic quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Code target iOS hay platform Apple nào?
- Optional có được xử lý rõ không?
- Async flow có khớp lifecycle không?
- Framework Apple nào đang được dùng?

## Failure Modes / Cách nó gây lỗi

- Force unwrap nil gây crash.
- Async task sống quá lifecycle mong muốn.
- Target/platform setting sai.
- Interop với framework Apple không rõ permission/lifecycle.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không target Apple platform thì chưa cần Swift.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[iOS]] vì Swift thường dùng để viết iOS app.
- [[Xcode]] vì Swift thường được build bằng Xcode.
- [[UIKit]] vì Swift có thể dùng để viết UIKit UI.

## Liên quan rộng

- Apple development
- Native mobile
- Static typing

## Keywords / Từ khóa tìm kiếm

- Swift
- Swift language
- iOS Swift
- optional
- async await
- Swift debugging

## Source trace

- Swift documentation
- Apple Developer documentation
