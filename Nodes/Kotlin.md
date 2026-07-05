# Kotlin

Aliases: Kotlin

Type: Mobile Development

## Context / Ngữ cảnh

Kotlin xuất hiện khi phát triển Android app hoặc JVM service cần ngôn ngữ hiện đại, null-safety và coroutine.

## Boundary / Ranh giới

### Nó là gì

Kotlin là ngôn ngữ lập trình chạy trên JVM và là lựa chọn phổ biến cho Android development.

### Nó không phải là gì

Kotlin không phải Android framework. Android là platform; Kotlin là ngôn ngữ dùng để viết code.

## Core Mechanism / Cơ chế lõi

Kotlin compile thành bytecode JVM hoặc target khác. Nó có null-safety, data class, extension function, coroutine và interop với Java.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Android code, coroutine, nullability, build Gradle hoặc interop Java/Kotlin.

## Output / Artifact nên có

- Kotlin source/module
- Gradle config
- Coroutine/threading note
- Nullability convention
- Test cho logic quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Code chạy trên Android hay JVM backend?
- Coroutine scope có đúng lifecycle không?
- Nullability có được xử lý rõ không?
- Java interop có tạo risk không?

## Failure Modes / Cách nó gây lỗi

- Coroutine scope sai làm task sống quá lâu.
- Nullability xử lý sai gây crash.
- Blocking call chạy sai thread.
- Java interop làm type/null contract không rõ.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không dùng Android/JVM thì chưa cần Kotlin.
- Không nên dùng coroutine phức tạp nếu flow đồng bộ đơn giản đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[APK]] vì Android app viết bằng Kotlin thường đóng gói thành APK.
- [[AAB]] vì Android release hiện đại thường dùng app bundle.
- [[ANR]] vì Kotlin Android code có thể gây hoặc tránh ANR.

## Liên quan rộng

- Android development
- JVM
- Coroutine

## Keywords / Từ khóa tìm kiếm

- Kotlin
- Android Kotlin
- coroutine
- null safety
- data class
- Gradle Kotlin
- Kotlin debugging

## Source trace

- Kotlin documentation
- Android Developers documentation
