# Draw Call

Aliases: Draw Call, draw call

Type: Game Development

## Context / Ngữ cảnh

Draw Call xuất hiện khi game/rendering cần gửi lệnh vẽ từ CPU sang GPU để render mesh, sprite, UI hoặc batch object lên frame.

## Boundary / Ranh giới

### Nó là gì

Draw Call là một lệnh hoặc nhóm lệnh render mà CPU gửi cho GPU để vẽ geometry/material/state nhất định.

### Nó không phải là gì

Draw Call không phải số lượng object duy nhất. Nhiều object có thể được batch thành ít draw call, hoặc một object có thể tạo nhiều draw call nếu có nhiều material/pass.

## Core Mechanism / Cơ chế lõi

Renderer gom object theo material, mesh, shader, texture, render state và batching rule. Mỗi lần cần đổi state hoặc submit batch, CPU tạo draw call; GPU xử lý vertex/pixel theo pipeline.

## Project Role / Vai trò trong dự án

Dùng node này khi debug FPS thấp, CPU render bottleneck, UI quá nặng, sprite batching, material count hoặc scene có quá nhiều object nhỏ.

## Output / Artifact nên có

- Frame profiler capture
- Draw call count
- Batching/material breakdown
- CPU/GPU bottleneck note
- Optimization decision

## Decision Checklist / Câu hỏi kiểm tra

- Bottleneck nằm ở CPU submit hay GPU shading?
- Object có dùng chung material/texture không?
- Có batching/instancing được không?
- UI hoặc particle có tạo draw call dư không?
- Draw call giảm có thật sự tăng FPS không?

## Failure Modes / Cách nó gây lỗi

- Quá nhiều material phá batching.
- Mỗi sprite/UI element tạo draw call riêng.
- Tập trung giảm draw call nhưng bottleneck thật là shader/GPU.
- Batching làm memory tăng hoặc phá behavior dynamic.
- Editor view khác build target nên đo sai.

## Khi nào chưa cần hoặc dễ over-engineer

- Scene nhỏ hoặc FPS ổn thì chưa cần tối ưu draw call.
- Không nên batch phức tạp trước khi có profiler xác nhận bottleneck.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Shader]] vì shader/material state ảnh hưởng draw call.
- [[Sprite]] vì sprite batching liên quan trực tiếp draw call.
- [[Performance Optimization]] vì draw call count ảnh hưởng frame time.
- [[Game Build]] vì đo performance nên kiểm tra trên build thật.

## Liên quan rộng

- Rendering pipeline
- Batching
- GPU profiling

## Keywords / Từ khóa tìm kiếm

- Draw Call
- draw call
- batching
- instancing
- material state
- frame profiler
- draw call debugging

## Source trace

- Unity documentation
- Unreal Engine documentation
- GPU profiling references
