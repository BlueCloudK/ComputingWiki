# Gradle

Aliases: Gradle

Type: Frameworks and Tools

## Context / Ngữ cảnh

Gradle xuất hiện khi JVM/Android project cần build automation linh hoạt, dependency management và task pipeline mạnh hơn convention cố định.

## Boundary / Ranh giới

### Nó là gì

Gradle là build automation tool dùng task graph và script cấu hình bằng Kotlin DSL hoặc Groovy DSL.

### Nó không phải là gì

Gradle không phải Java/Kotlin runtime và không phải Android SDK. Nó điều phối build, test, package và dependency.

## Core Mechanism / Cơ chế lõi

Gradle đọc build script, tạo task graph, resolve dependency, chạy task cần thiết và tạo artifact. Nó hỗ trợ incremental build, build cache, plugin và multi-project build.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Android/JVM build, dependency conflict, plugin, build cache, task order hoặc CI build.

## Output / Artifact nên có

- `build.gradle` hoặc `build.gradle.kts`
- Plugin/dependency list
- Task list quan trọng
- Wrapper version
- CI build command

## Decision Checklist / Câu hỏi kiểm tra

- Project dùng Gradle wrapper version nào?
- Plugin/dependency có pin rõ không?
- Task nào tạo artifact chính?
- Build cache có ảnh hưởng output không?
- Local và CI có dùng cùng command không?

## Failure Modes / Cách nó gây lỗi

- Plugin version lệch làm build fail.
- Dependency conflict gây runtime lỗi.
- Task dependency thiếu làm output cũ.
- Cache sai làm build khó debug.
- Wrapper/local Gradle version không khớp.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ không JVM/Android có thể không cần Gradle.
- Không nên viết custom task phức tạp nếu plugin chuẩn đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kotlin]] vì Gradle Kotlin DSL và Android Kotlin project rất phổ biến.
- [[AAB]] vì Android release bundle thường build bằng Gradle.
- [[APK]] vì Android APK thường build bằng Gradle.
- [[Build Cache]] vì Gradle có incremental build/cache mạnh.
- [[CI]] vì Gradle build thường chạy trong pipeline.

## Liên quan rộng

- JVM build
- Android build
- Dependency management

## Keywords / Từ khóa tìm kiếm

- Gradle
- build.gradle
- Gradle Kotlin DSL
- Gradle task
- Gradle wrapper
- Android Gradle
- Gradle debugging

## Source trace

- Gradle documentation
- Android Developers documentation
