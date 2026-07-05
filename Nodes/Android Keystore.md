# Android Keystore

Aliases: Android Keystore, Android Keystore System

Type: Mobile Development

## Context / Ngữ cảnh

Android Keystore xuất hiện khi Android app cần tạo, lưu hoặc dùng cryptographic key mà không muốn key material bị lộ trực tiếp trong app storage.

## Boundary / Ranh giới

### Nó là gì

Android Keystore là hệ thống của Android để lưu và sử dụng key cryptography trong container được OS/hardware bảo vệ tùy thiết bị.

### Nó không phải là gì

Android Keystore không phải nơi lưu mọi secret dạng text. Nó chủ yếu quản lý key; dữ liệu như token/password thường cần được mã hóa hoặc lưu qua secure storage phù hợp.

## Core Mechanism / Cơ chế lõi

App tạo hoặc import key với alias và policy. Khi cần encrypt/decrypt/sign, app yêu cầu Keystore thực hiện operation bằng key đó. Key có thể bị ràng buộc bởi device lock, biometric, hardware-backed storage hoặc validity window.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế secure storage, mobile session token, encryption local, signing request hoặc debug lỗi key invalidated sau đổi lock/biometric/device restore.

## Output / Artifact nên có

- Key alias/purpose
- Algorithm và key size
- Authentication requirement
- Backup/restore behavior note
- Error handling for invalidated key

## Decision Checklist / Câu hỏi kiểm tra

- Key dùng để encrypt, decrypt, sign hay verify?
- Key có cần user authentication không?
- Key có hardware-backed không?
- Khi user đổi lock/biometric thì key xử lý ra sao?
- Dữ liệu mã hóa có backup/restore được không?

## Failure Modes / Cách nó gây lỗi

- Tưởng Keystore lưu token trực tiếp thay vì key.
- Key bị invalidated làm app không decrypt được dữ liệu cũ.
- Backup encrypted data nhưng không backup/restore được key.
- Dùng alias trùng hoặc rotate key không có migration.
- Fallback insecure khi Keystore operation fail.

## Khi nào chưa cần hoặc dễ over-engineer

- Dữ liệu không nhạy cảm có thể không cần Keystore.
- Không nên tự thiết kế crypto phức tạp nếu secure storage library/platform API đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Secret]] vì Android Keystore giúp bảo vệ key/secret boundary.
- [[Mobile Session]] vì session token local thường liên quan secure storage.
- [[Kotlin]] vì Android implementation thường viết bằng Kotlin.
- [[Authentication]] vì key có thể gắn với device/user authentication.

## Liên quan rộng

- Secure storage
- Mobile cryptography
- Hardware-backed key

## Keywords / Từ khóa tìm kiếm

- Android Keystore
- Android Keystore System
- secure storage Android
- hardware-backed key
- key invalidated
- mobile encryption
- Android Keystore debugging

## Source trace

- Android Developers documentation
- OWASP Mobile guidance
