# AAB

Aliases: AAB, Android App Bundle

Type: Mobile Development

## Context / Ngữ cảnh

AAB xuất hiện khi Android app cần artifact release tối ưu cho Google Play distribution.

## Boundary / Ranh giới

### Nó là gì

AAB là Android App Bundle, định dạng build chứa module và resource để store tạo APK phù hợp từng thiết bị.

### Nó không phải là gì

AAB không phải file cài trực tiếp phổ biến như APK. Nó thường đi qua store hoặc tool tạo APK từ bundle.

## Core Mechanism / Cơ chế lõi

Build system tạo app bundle từ code/resource/manifest. Store dùng bundle để sinh APK split theo thiết bị, ABI, density hoặc language nhằm giảm dung lượng tải xuống.

## Project Role / Vai trò trong dự án

Dùng node này khi debug release Android, upload store, signing, versioning hoặc khác biệt giữa local APK và store-delivered app.

## Output / Artifact nên có

- AAB release artifact
- Signing/upload key note
- Version code/name
- Store track/release note
- Bundle validation checklist

## Decision Checklist / Câu hỏi kiểm tra

- AAB build cho track nào?
- Signing config có đúng không?
- Version code có tăng không?
- Dynamic feature/split có ảnh hưởng thiết bị nào không?
- Store validation có pass không?

## Failure Modes / Cách nó gây lỗi

- Signing key sai làm upload hoặc update fail.
- Version code không tăng.
- Resource/split chỉ lỗi trên một nhóm thiết bị.
- Local APK test pass nhưng bundle release lỗi.

## Khi nào chưa cần hoặc dễ over-engineer

- Test nội bộ nhanh có thể dùng APK debug trước.
- Không nên xử lý release bundle trước khi app chưa có release flow.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[APK]] vì APK có thể được sinh ra từ app bundle.
- [[Kotlin]] vì nhiều Android app viết bằng Kotlin.
- [[Mobile App]] vì AAB là artifact release Android app.

## Liên quan rộng

- Android release
- Play Store distribution
- App signing

## Keywords / Từ khóa tìm kiếm

- AAB
- Android App Bundle
- app bundle
- Android release
- split APK
- Play Store upload
- AAB debugging

## Source trace

- Android Developers documentation
