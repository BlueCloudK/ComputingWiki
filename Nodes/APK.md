# APK

Aliases: APK, Android Package

Type: Mobile Development

## Context / Ngữ cảnh

APK xuất hiện khi Android app cần được đóng gói để cài đặt, test hoặc phát hành ngoài store flow nhất định.

## Boundary / Ranh giới

### Nó là gì

APK là file package cài đặt Android app. Nó chứa code, resource, manifest và signature cần thiết để thiết bị Android cài app.

### Nó không phải là gì

APK không phải source code và không phải định dạng publish chính duy nhất trên Play Store hiện đại.

## Core Mechanism / Cơ chế lõi

Build system compile code/resource, tạo package, ký bằng signing key rồi sinh APK. Thiết bị kiểm tra package name, version, signature và manifest khi cài hoặc cập nhật.

## Project Role / Vai trò trong dự án

Dùng node này khi debug build Android, cài app test, signing, versionCode, permission hoặc lỗi install/update.

## Output / Artifact nên có

- APK build artifact
- Signing config
- Version code/name
- Manifest/permission note
- Install/test checklist

## Decision Checklist / Câu hỏi kiểm tra

- APK build cho debug hay release?
- Signing key có đúng không?
- Version code có tăng không?
- Manifest permission có đúng không?
- Thiết bị target có tương thích không?

## Failure Modes / Cách nó gây lỗi

- Signature khác làm update app fail.
- Version code không tăng nên không update được.
- Permission hoặc manifest sai làm runtime lỗi.
- Build debug/release bị nhầm.

## Khi nào chưa cần hoặc dễ over-engineer

- Nếu chỉ publish qua store hiện đại, AAB thường là artifact chính hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AAB]] vì AAB và APK đều là artifact release Android.
- [[Kotlin]] vì nhiều Android app viết bằng Kotlin.
- [[Mobile App]] vì APK là artifact cài đặt app Android.

## Liên quan rộng

- Android release
- App signing
- Mobile testing

## Keywords / Từ khóa tìm kiếm

- APK
- Android Package
- Android app package
- APK signing
- versionCode
- Android install
- APK debugging

## Source trace

- Android Developers documentation
