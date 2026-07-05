# Maven

Aliases: Maven, Apache Maven

Type: Frameworks and Tools

## Context / Ngữ cảnh

Maven xuất hiện khi Java project cần quản lý dependency, build lifecycle, test và packaging theo convention ổn định.

## Boundary / Ranh giới

### Nó là gì

Maven là build automation và dependency management tool cho Java/JVM project, dùng `pom.xml` làm cấu hình chính.

### Nó không phải là gì

Maven không phải Java runtime và không phải framework application như Spring.

## Core Mechanism / Cơ chế lõi

Maven đọc `pom.xml`, resolve dependency từ repository, chạy lifecycle phase như compile, test, package, verify và tạo artifact như JAR/WAR.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Java build, dependency conflict, test phase, packaging, CI hoặc release artifact.

## Output / Artifact nên có

- `pom.xml`
- Dependency/plugin list
- Build lifecycle command
- Artifact output note
- CI command

## Decision Checklist / Câu hỏi kiểm tra

- Dependency version có rõ không?
- Plugin build/test có đúng phase không?
- Artifact cần JAR hay WAR?
- Local và CI có dùng cùng command không?
- Java version có khớp project không?

## Failure Modes / Cách nó gây lỗi

- Dependency conflict làm runtime lỗi.
- Plugin version không pin gây build lệch.
- Test bị skip ngoài ý muốn.
- Java version local khác CI.
- Artifact package sai loại.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không dùng Java/JVM thì chưa cần Maven.
- Không nên thêm plugin phức tạp nếu lifecycle chuẩn đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Java]] vì Maven thường dùng cho Java project.
- [[CI]] vì Maven build/test thường chạy trong pipeline.
- [[Build Cache]] vì Maven dependency cache ảnh hưởng CI speed.
- [[CLI Tool]] vì Maven thường chạy qua CLI command.

## Liên quan rộng

- Java build
- Dependency management
- Artifact packaging

## Keywords / Từ khóa tìm kiếm

- Maven
- Apache Maven
- pom.xml
- mvn test
- mvn package
- Java dependency
- Maven debugging

## Source trace

- Maven documentation
