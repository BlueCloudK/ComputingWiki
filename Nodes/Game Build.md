# Game Build

Aliases: Game Build, game build

Type: Game Development

## Context / Ngữ cảnh

Game Build xuất hiện khi project game cần được đóng gói thành bản chạy được cho tester, player, store, platform hoặc CI release pipeline.

## Boundary / Ranh giới

### Nó là gì

Game Build là artifact hoặc process tạo ra executable/package của game từ source code, asset, engine config, platform setting và build profile.

### Nó không phải là gì

Game Build không phải source project trong editor. Editor play mode có thể chạy được nhưng chưa chứng minh build thật ổn trên target platform.

## Core Mechanism / Cơ chế lõi

Build pipeline lấy code, scene, asset, shader, platform setting và dependency, rồi compile/package thành artifact như desktop executable, APK/AAB, IPA, WebGL build hoặc console package.

## Project Role / Vai trò trong dự án

Dùng node này khi debug build fail, asset thiếu trong build, platform config sai, performance khác editor hoặc chuẩn bị release/test build.

## Output / Artifact nên có

- Build artifact
- Target platform/profile
- Build config/version
- Included scene/asset list
- Smoke test checklist

## Decision Checklist / Câu hỏi kiểm tra

- Build target là platform nào?
- Build dùng debug, development hay release profile?
- Scene/asset cần thiết có được include không?
- Version/build number có trace được commit không?
- Build đã chạy smoke test trên target chưa?

## Failure Modes / Cách nó gây lỗi

- Chạy ổn trong editor nhưng build thiếu asset/scene.
- Platform setting sai làm input/render/storage lỗi.
- Development build bị đưa nhầm cho release.
- Shader/asset compile khác giữa platform.
- Build artifact không trace được source commit.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype gameplay cực sớm có thể test trong editor trước.
- Không nên tối ưu release pipeline khi core loop chưa ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Asset Pipeline]] vì asset phải được import/package vào build.
- [[Platform Porting]] vì build thay đổi theo target platform.
- [[Release Artifact]] vì game build là artifact phát hành/test.
- [[Performance Optimization]] vì performance build thật mới đáng tin.

## Liên quan rộng

- Build pipeline
- Game release
- Platform target

## Keywords / Từ khóa tìm kiếm

- Game Build
- game build
- build artifact
- development build
- release build
- platform build
- game build debugging

## Source trace

- Unity documentation
- Unreal Engine documentation
- Godot documentation
