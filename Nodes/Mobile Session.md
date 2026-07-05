# Mobile Session

Aliases: Mobile Session, app session

Type: Mobile Development

## Context / Ngữ cảnh

Mobile Session xuất hiện khi app mobile cần duy trì trạng thái đăng nhập, user context, token, navigation state hoặc analytics session qua nhiều lần foreground/background.

## Boundary / Ranh giới

### Nó là gì

Mobile Session là vòng đời trạng thái người dùng/app trên thiết bị mobile, thường liên quan auth token, refresh, secure storage, app lifecycle và session timeout.

### Nó không phải là gì

Mobile Session không chỉ là HTTP session truyền thống. Mobile app có lifecycle offline/background, token storage và network không ổn định riêng.

## Core Mechanism / Cơ chế lõi

App lưu session credential/context trong secure storage, refresh token khi cần, xử lý foreground/background, expire/logout và đồng bộ state với backend theo policy.

## Project Role / Vai trò trong dự án

Dùng node này khi debug app tự logout, token hết hạn, refresh fail, session restore, offline mode hoặc behavior khác nhau giữa Android/iOS.

## Output / Artifact nên có

- Session state diagram
- Token/storage policy
- Expire/refresh rule
- App lifecycle handling
- Logout/revoke flow

## Decision Checklist / Câu hỏi kiểm tra

- Session sống bao lâu?
- Token được lưu ở đâu?
- Refresh xảy ra khi nào?
- App background/foreground xử lý session ra sao?
- Logout có revoke server-side không?

## Failure Modes / Cách nó gây lỗi

- Token lưu không an toàn.
- Refresh race làm user logout ngẫu nhiên.
- App resume dùng token hết hạn.
- Offline state không rõ làm UI sai.
- Android/iOS lifecycle xử lý khác nhau.

## Khi nào chưa cần hoặc dễ over-engineer

- App không đăng nhập hoặc chỉ demo local chưa cần session policy phức tạp.
- Không nên tự xây auth/session flow nếu platform SDK chuẩn đã đủ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Session Management]] vì mobile session là session management trong mobile app.
- [[Authentication]] vì session thường bắt đầu từ login/auth.
- [[Secret]] vì token/credential là secret cần bảo vệ.
- [[iOS]] vì lifecycle/storage iOS ảnh hưởng session behavior.

## Liên quan rộng

- Mobile auth
- Secure storage
- App lifecycle

## Keywords / Từ khóa tìm kiếm

- Mobile Session
- app session
- mobile auth session
- refresh token
- secure storage
- app lifecycle session
- mobile session debugging

## Source trace

- Android Developers documentation
- Apple Developer documentation
- OWASP Mobile guidance
