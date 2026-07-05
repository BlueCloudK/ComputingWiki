# Flutter

Aliases: Flutter

Type: Mobile Development

## Context / Ngữ cảnh

Flutter xuất hiện khi app cần xây UI đa nền tảng từ cùng một codebase, thường cho Android, iOS, web hoặc desktop.

## Boundary / Ranh giới

### Nó là gì

Flutter là UI toolkit dùng Dart để xây app đa nền tảng bằng widget tree.

### Nó không phải là gì

Flutter không phải Dart. Dart là ngôn ngữ; Flutter là framework/toolkit dùng Dart.

## Core Mechanism / Cơ chế lõi

App Flutter được tổ chức bằng widget. State thay đổi làm widget tree rebuild phần cần thiết. Build tool tạo artifact cho từng platform như APK, AAB hoặc iOS package.

## Project Role / Vai trò trong dự án

Dùng node này khi debug widget tree, state, navigation, platform build, plugin native hoặc performance trong app Flutter.

## Output / Artifact nên có

- Widget tree
- State ownership map
- Navigation flow
- Platform build note
- Plugin/native dependency list
- Test cho flow quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- State nằm ở widget nào?
- Navigation flow có rõ không?
- Target platform là gì?
- Build artifact cần APK, AAB hay iOS package?
- Plugin native có config riêng Android/iOS không?

## Failure Modes / Cách nó gây lỗi

- Widget rebuild quá rộng làm UI chậm.
- State đặt sai chỗ làm UI lệch.
- Platform config sai làm build fail.
- Plugin native gây lỗi riêng theo Android/iOS.
- Work nặng không tách isolate làm UI chậm.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không cần đa nền tảng hoặc mobile UI thì chưa cần Flutter.
- Không nên chọn Flutter chỉ để tránh hiểu native platform boundary.

## Gồm những gì

- [[Dart]]

## Nối mạnh

- [[Dart]] vì Flutter app viết bằng Dart.
- [[APK]] vì Flutter Android có thể build APK.
- [[AAB]] vì Flutter Android release thường dùng AAB.
- [[iOS]] vì Flutter cũng target iOS.
- [[Performance Optimization]] vì rebuild và native plugin có thể ảnh hưởng frame time.

## Liên quan rộng

- Cross-platform app
- Widget tree
- Mobile UI

## Keywords / Từ khóa tìm kiếm

- Flutter
- Flutter app
- widget tree
- Flutter state
- Flutter plugin
- Flutter build
- Flutter debugging

## Source trace

- Flutter documentation
- Dart documentation
