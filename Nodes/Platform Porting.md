# Platform Porting

Aliases: Platform Porting, porting

Type: Game Development

## Context / Ngữ cảnh

Platform Porting xuất hiện khi game/app đã chạy trên một platform nhưng cần đưa sang platform khác như PC, mobile, console, web hoặc operating system khác.

## Boundary / Ranh giới

### Nó là gì

Platform Porting là quá trình điều chỉnh build, input, rendering, performance, storage, networking, permission và distribution để phần mềm chạy đúng trên platform mới.

### Nó không phải là gì

Platform Porting không chỉ là compile lại source code. Platform mới thường có constraint khác về hardware, API, UX, file system, input và release rule.

## Core Mechanism / Cơ chế lõi

Team xác định platform-specific boundary, tách abstraction, thay adapter/build config, test behavior trên device thật, rồi xử lý performance và compliance/release requirement.

## Project Role / Vai trò trong dự án

Dùng node này khi đưa game từ desktop sang mobile/web, từ engine build này sang platform khác, hoặc debug lỗi chỉ xảy ra ở một platform.

## Output / Artifact nên có

- Platform compatibility matrix
- Build target config
- Input/rendering/storage adapter note
- Device/performance test checklist
- Release/compliance note

## Decision Checklist / Câu hỏi kiểm tra

- Platform mới khác gì về input, screen, storage và permission?
- Rendering/API có tương thích không?
- Performance target là FPS/latency nào?
- Asset format/size có cần đổi không?
- Release package và store rule là gì?

## Failure Modes / Cách nó gây lỗi

- Code build được nhưng input/UI không hợp platform.
- Asset quá nặng cho mobile/web.
- File path/storage assumption sai.
- Performance chỉ pass trên máy dev, fail trên device thật.
- Platform-specific code rải khắp nơi làm maintain khó.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype chưa ổn core gameplay thì chưa cần port nhiều platform.
- Không nên abstract quá sớm nếu chưa biết platform target thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Game Loop]] vì porting có thể ảnh hưởng frame/update timing.
- [[Asset Pipeline]] vì asset thường phải đóng gói/tối ưu theo platform.
- [[Performance Optimization]] vì platform mới thường có budget khác.
- [[ABI]] vì native/platform boundary có thể liên quan binary compatibility.

## Liên quan rộng

- Cross-platform build
- Device compatibility
- Game release

## Keywords / Từ khóa tìm kiếm

- Platform Porting
- porting
- cross-platform game
- platform-specific code
- device compatibility
- platform build
- porting debugging

## Source trace

- Game Programming Patterns
- Unity documentation
- Unreal Engine documentation
