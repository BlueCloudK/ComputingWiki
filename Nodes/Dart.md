# Dart

Aliases: Dart

Type: Mobile Development

## Context / Ngữ cảnh

Dart xuất hiện khi phát triển app với Flutter hoặc cần ngôn ngữ client-side có static typing, async và tooling rõ.

## Boundary / Ranh giới

### Nó là gì

Dart là ngôn ngữ lập trình do Google phát triển, thường dùng với Flutter để xây app đa nền tảng.

### Nó không phải là gì

Dart không phải Flutter. Dart là ngôn ngữ; Flutter là UI framework/toolkit dùng Dart.

## Core Mechanism / Cơ chế lõi

Dart code được compile hoặc JIT/AOT tùy môi trường. Nó có static typing, async/await, isolate, package system và runtime/toolchain riêng.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Flutter code, async flow, package dependency, build mobile hoặc logic viết bằng Dart.

## Output / Artifact nên có

- Dart source/module
- Package dependency note
- Async/isolate note nếu cần
- Test cho logic quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Code chạy trong Flutter hay Dart runtime khác?
- Async flow có xử lý error đúng không?
- Package version có pin rõ không?
- Logic có test chưa?

## Failure Modes / Cách nó gây lỗi

- Async error bị bỏ qua.
- State/UI update sai lifecycle trong Flutter.
- Package version lệch làm build fail.
- Work nặng không tách isolate làm UI chậm.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không dùng Flutter/Dart thì chưa cần Dart.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Mobile App]] vì Dart thường dùng trong app mobile Flutter.
- [[SDK]] vì Dart đi kèm SDK/toolchain riêng.
- [[Performance Optimization]] vì work nặng trong UI app cần tối ưu đúng boundary.

## Liên quan rộng

- Flutter ecosystem
- Mobile development
- Async programming

## Keywords / Từ khóa tìm kiếm

- Dart
- Dart language
- Flutter Dart
- async await
- isolate
- Dart package
- Dart debugging

## Source trace

- Dart documentation
- Flutter documentation
