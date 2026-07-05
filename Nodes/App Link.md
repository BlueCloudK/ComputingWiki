# App Link

Aliases: App Link, Deep Link, Universal Link

Type: Mobile Development

## Context / Ngữ cảnh

App Link xuất hiện khi URL hoặc external intent cần mở đúng màn hình trong mobile app thay vì chỉ mở web browser.

## Boundary / Ranh giới

### Nó là gì

App Link là cơ chế liên kết URL/domain với app mobile để route người dùng vào app và màn hình cụ thể. Trên Android thường gọi là App Links; trên iOS thường tương ứng với Universal Links.

### Nó không phải là gì

App Link không chỉ là route nội bộ trong app. Nó cần cấu hình platform, domain verification, manifest/entitlement và fallback khi app chưa cài.

## Core Mechanism / Cơ chế lõi

Platform nhận URL/intent, kiểm tra domain association/verification, mở app nếu hợp lệ, rồi app parse path/query và điều hướng tới screen tương ứng.

## Project Role / Vai trò trong dự án

Dùng node này khi debug link không mở app, mở sai screen, login redirect, campaign link, payment callback hoặc cross-platform mobile navigation.

## Output / Artifact nên có

- Domain/path mapping
- Android manifest intent-filter
- iOS associated domains config
- Fallback web behavior
- Test matrix: installed/not installed/login state

## Decision Checklist / Câu hỏi kiểm tra

- Domain đã verify với app chưa?
- Path nào được app handle?
- User chưa login thì redirect ra sao?
- App chưa cài thì fallback đi đâu?
- Android/iOS behavior có giống nhau không?

## Failure Modes / Cách nó gây lỗi

- Domain association file sai làm link mở browser.
- Path parser sai làm mở nhầm screen.
- Login flow mất deep link target.
- Multiple app/environment cùng domain gây conflict.
- Test chỉ trên app đã cài, bỏ qua fallback.

## Khi nào chưa cần hoặc dễ over-engineer

- App chưa cần external entry point thì chưa cần app link.
- Không nên thêm nhiều scheme/path nếu navigation và auth flow chưa ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Route]] vì app link cần map URL tới route/screen.
- [[Mobile Session]] vì login/session state ảnh hưởng deep link handling.
- [[iOS]] vì Universal Links cần config phía iOS.
- [[HTTPS]] vì domain verification thường dựa trên HTTPS-hosted association file.

## Liên quan rộng

- Deep linking
- Universal Links
- Mobile navigation

## Keywords / Từ khóa tìm kiếm

- App Link
- Deep Link
- Universal Link
- Android App Links
- associated domains
- mobile deep linking
- app link debugging

## Source trace

- Android Developers documentation
- Apple Developer documentation
