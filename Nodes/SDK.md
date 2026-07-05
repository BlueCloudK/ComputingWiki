# SDK

Aliases: SDK, Software Development Kit

Type: Frameworks and Tools

## Context / Ngữ cảnh

SDK xuất hiện khi developer cần bộ công cụ chính thức để build app hoặc tích hợp với một platform/API cụ thể.

## Boundary / Ranh giới

### Nó là gì

SDK là bộ công cụ phát triển gồm library, API wrapper, compiler/tooling, emulator, docs, sample hoặc CLI tùy platform.

### Nó không phải là gì

SDK không phải chỉ là documentation. Nó thường chứa code/tool thật ảnh hưởng build, runtime và compatibility.

## Core Mechanism / Cơ chế lõi

Project cài SDK đúng version, cấu hình path/toolchain, import library hoặc gọi CLI/API, rồi build/test theo target platform.

## Project Role / Vai trò trong dự án

Dùng node này khi setup môi trường dev, debug version mismatch, platform integration, mobile build hoặc cloud/API client.

## Output / Artifact nên có

- SDK version note
- Install/setup instruction
- Environment path/config
- Compatibility matrix
- Sample/test command

## Decision Checklist / Câu hỏi kiểm tra

- SDK version có khớp project không?
- Toolchain path có đúng không?
- CI và local dùng cùng version không?
- SDK có breaking change gì không?
- Credential/config có nằm đúng boundary không?

## Failure Modes / Cách nó gây lỗi

- Local dùng SDK khác CI.
- Path/toolchain config sai.
- SDK update gây breaking change.
- Sample chạy được nhưng project config thật fail.

## Khi nào chưa cần hoặc dễ over-engineer

- Nếu chỉ gọi HTTP API đơn giản, có thể chưa cần SDK nặng.
- Không nên pin SDK quá cũ nếu security/compatibility đã hết hỗ trợ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[IDE]] vì IDE thường cần biết SDK/toolchain.
- [[CLI Tool]] vì nhiều SDK đi kèm CLI.
- [[CI]] vì pipeline cần cài đúng SDK version.
- [[iOS]] vì iOS development phụ thuộc Apple SDK.

## Liên quan rộng

- Toolchain
- Platform integration
- Developer environment

## Keywords / Từ khóa tìm kiếm

- SDK
- Software Development Kit
- SDK version
- toolchain
- platform SDK
- SDK debugging

## Source trace

- Apple Developer documentation
- Android Developers documentation
- .NET documentation
