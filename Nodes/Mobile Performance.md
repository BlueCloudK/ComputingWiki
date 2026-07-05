# Mobile Performance

Aliases: Mobile Performance, mobile app performance

Type: Mobile Development

## Context / Ngữ cảnh

Mobile Performance xuất hiện khi app mobile cần giữ UI mượt, startup nhanh, network hợp lý, pin/CPU thấp và ổn định trên nhiều thiết bị thật.

## Boundary / Ranh giới

### Nó là gì

Mobile Performance là tập hợp chỉ số và kỹ thuật tối ưu app mobile: startup time, frame time, memory, battery, network, disk I/O, ANR/crash và responsiveness.

### Nó không phải là gì

Mobile Performance không chỉ là FPS. App có thể render mượt nhưng startup chậm, tốn pin, leak memory hoặc bị ANR trên thiết bị yếu.

## Core Mechanism / Cơ chế lõi

App mobile chạy trên thiết bị có CPU/GPU/RAM/pin/network giới hạn. Work nặng trên main thread, asset lớn, re-render dư, network chatty hoặc memory leak đều làm user thấy chậm/đơ/nóng máy.

## Project Role / Vai trò trong dự án

Dùng node này khi debug app lag, startup lâu, scroll giật, pin tụt, memory tăng, ANR, bundle lớn hoặc performance khác giữa debug/release/device.

## Output / Artifact nên có

- Performance profile trên device thật
- Startup/frame/memory/network metric
- Bottleneck hypothesis
- Before/after comparison
- Device matrix test note

## Decision Checklist / Câu hỏi kiểm tra

- Bottleneck là CPU, GPU, memory, network hay disk?
- Đo trên debug hay release build?
- Thiết bị test có đại diện user thật không?
- Work nào đang chạy trên main thread?
- Optimization có cải thiện metric hay chỉ cảm giác?

## Failure Modes / Cách nó gây lỗi

- Chỉ test trên máy mạnh nên bỏ sót low-end device.
- Debug build chậm nhưng kết luận sai cho release.
- Tối ưu render trong khi bottleneck là network/startup.
- Memory leak chỉ lộ sau dùng lâu.
- Cache quá nhiều làm memory/pin tệ hơn.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype sớm có thể đo nhẹ trước, chưa cần tối ưu sâu.
- Không nên tối ưu micro trước khi profiler chỉ ra bottleneck thật.

## Gồm những gì

- [[ANR]]

## Nối mạnh

- [[ANR]] vì ANR là failure mode quan trọng của mobile performance.
- [[Performance Optimization]] vì mobile performance là một nhánh tối ưu hiệu năng.
- [[Flutter]] vì Flutter app có vấn đề frame/rebuild/platform channel riêng.
- [[React Native]] vì React Native app có bridge/runtime performance concern riêng.

## Liên quan rộng

- Startup time
- Frame time
- Battery usage
- Memory pressure

## Keywords / Từ khóa tìm kiếm

- Mobile Performance
- mobile app performance
- startup time
- frame time
- memory leak
- battery usage
- mobile performance debugging

## Source trace

- Android Developers documentation
- Apple Developer documentation
- Flutter documentation
- React Native documentation
