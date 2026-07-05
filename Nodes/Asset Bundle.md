# Asset Bundle

Aliases: Asset Bundle, asset pack

Type: Game Development

## Context / Ngữ cảnh

Asset Bundle xuất hiện khi game cần đóng gói asset để tải theo phiên bản, theo màn chơi, theo DLC hoặc tải động sau khi app/game đã phát hành.

## Boundary / Ranh giới

### Nó là gì

Asset Bundle là artifact chứa asset đã build/import theo định dạng engine/platform để runtime có thể load khi cần.

### Nó không phải là gì

Asset Bundle không phải source asset gốc trong project. Nó là output build của asset pipeline và cần version, dependency, cache rule rõ.

## Core Mechanism / Cơ chế lõi

Asset pipeline import texture, prefab, scene, material, shader hoặc audio; gom chúng thành bundle; runtime tải bundle từ local/remote, resolve dependency rồi instantiate/use asset.

## Project Role / Vai trò trong dự án

Dùng node này khi debug asset thiếu, version mismatch, remote content update, memory tăng do bundle không unload hoặc build khác nhau giữa platform.

## Output / Artifact nên có

- Bundle manifest
- Asset-to-bundle mapping
- Version/hash rule
- Dependency list
- Load/unload test checklist

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào nằm trong bundle nào?
- Bundle có version/hash không?
- Dependency giữa bundle có rõ không?
- Runtime load/unload ở thời điểm nào?
- Cache remote content xử lý ra sao?

## Failure Modes / Cách nó gây lỗi

- Bundle thiếu dependency làm asset load fail.
- Version mismatch khiến client tải asset sai.
- Không unload bundle làm memory tăng.
- Platform build khác nhau làm shader/material lỗi.
- Bundle quá lớn làm loading time cao.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype nhỏ có thể pack asset trực tiếp trong build.
- Không nên dùng bundle/dynamic content nếu chưa có nhu cầu update hoặc memory/loading rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Asset Pipeline]] vì asset bundle là output của asset pipeline.
- [[Game Build]] vì bundle thường đi kèm build/release.
- [[Object Storage]] vì remote bundle thường được host trên object storage/CDN.
- [[CDN]] vì phân phối asset bundle cần cache/edge delivery.

## Liên quan rộng

- Remote content
- DLC
- Asset versioning
- Runtime loading

## Keywords / Từ khóa tìm kiếm

- Asset Bundle
- asset pack
- remote asset
- bundle manifest
- asset dependency
- runtime loading
- asset bundle debugging

## Source trace

- Unity documentation
- Unreal Engine documentation
- Godot documentation
