# NuGet

Aliases: NuGet

Type: Frameworks and Tools

## Context / Ngữ cảnh

NuGet xuất hiện khi .NET project cần quản lý package dependency, package restore, version và publish library.

## Boundary / Ranh giới

### Nó là gì

NuGet là package manager chính của .NET ecosystem.

### Nó không phải là gì

NuGet không phải .NET runtime và không phải build system đầy đủ. Build thường do `dotnet build` hoặc MSBuild điều phối.

## Core Mechanism / Cơ chế lõi

Project khai báo package reference trong project file. NuGet restore dependency từ feed, cache package local và cung cấp assembly cho build/runtime.

## Project Role / Vai trò trong dự án

Dùng node này khi debug .NET dependency, package restore, private feed, version conflict hoặc publish package.

## Output / Artifact nên có

- Package references
- NuGet feed/source config
- Lockfile nếu dùng
- Restore/build command
- Versioning convention

## Decision Checklist / Câu hỏi kiểm tra

- Package source là public hay private feed?
- Version có pin rõ không?
- CI restore có dùng đúng credential không?
- Dependency conflict có được phát hiện không?

## Failure Modes / Cách nó gây lỗi

- Private feed credential sai làm restore fail.
- Version conflict gây runtime lỗi.
- Package cache cũ làm local khác CI.
- Publish package sai version.

## Khi nào chưa cần hoặc dễ over-engineer

- Project không dùng .NET thì chưa cần NuGet.
- Không nên tạo private feed nếu package chưa cần chia sẻ ổn định.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì package restore/build cần chạy trong pipeline.
- [[Build Cache]] vì package cache ảnh hưởng tốc độ và reproducibility.
- [[SDK]] vì .NET SDK quyết định restore/build behavior.

## Liên quan rộng

- .NET ecosystem
- Package restore
- Dependency management

## Keywords / Từ khóa tìm kiếm

- NuGet
- NuGet package
- package restore
- private feed
- dotnet restore
- package reference
- NuGet debugging

## Source trace

- NuGet documentation
- .NET documentation
