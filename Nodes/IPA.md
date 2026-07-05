# IPA

Aliases: IPA, iOS App Store Package

Type: Mobile Development

## Context / Ngữ cảnh

IPA xuất hiện khi iOS app cần được đóng gói để test, phân phối nội bộ, đưa lên TestFlight hoặc phát hành trong hệ sinh thái Apple.

## Boundary / Ranh giới

### Nó là gì

IPA là file package của iOS app, thường được tạo từ archive build và chứa app bundle đã được ký bằng certificate/provisioning profile phù hợp.

### Nó không phải là gì

IPA không phải source code và không phải Xcode project. Nó là artifact sau build/sign/archive.

## Core Mechanism / Cơ chế lõi

Toolchain Apple build app, ký bằng certificate/provisioning profile, archive rồi export thành IPA theo distribution method như development, ad hoc, enterprise hoặc App Store.

## Project Role / Vai trò trong dự án

Dùng node này khi debug iOS release, signing, TestFlight, archive/export hoặc cài app trên thiết bị test.

## Output / Artifact nên có

- IPA artifact
- Signing/provisioning note
- Bundle id/version note
- Distribution method
- Install/test checklist

## Decision Checklist / Câu hỏi kiểm tra

- IPA build cho development, ad hoc, enterprise hay App Store?
- Certificate/profile có đúng không?
- Bundle id và version có đúng không?
- Thiết bị/test channel có được phép cài không?
- Archive/export config có khác debug build không?

## Failure Modes / Cách nó gây lỗi

- Signing sai làm app không cài được.
- Provisioning profile thiếu device/capability.
- Bundle id hoặc version sai.
- Archive/export config khác debug build.
- IPA được tạo từ branch/version không trace được.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa release/test iOS device thì chưa cần IPA.
- Simulator/debug build sớm có thể chưa cần packaging release đầy đủ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[iOS]] vì IPA là artifact phân phối iOS app.
- [[Xcode]] vì Xcode thường tạo archive/export IPA.
- [[Swift]] vì nhiều iOS app trong IPA viết bằng Swift.
- [[Release Artifact]] vì IPA là release artifact của iOS pipeline.

## Liên quan rộng

- iOS release
- App signing
- TestFlight

## Keywords / Từ khóa tìm kiếm

- IPA
- iOS app package
- iOS archive
- TestFlight
- provisioning profile
- app signing
- IPA debugging

## Source trace

- Apple Developer documentation
