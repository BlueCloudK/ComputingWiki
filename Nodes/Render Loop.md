# Render Loop

Aliases: Render Loop, rendering loop

Type: Game Development

## Context / Ngữ cảnh

Render Loop xuất hiện khi game/engine cần tạo từng frame bằng cách cập nhật scene, chuẩn bị camera/render state và gửi lệnh vẽ tới GPU.

## Boundary / Ranh giới

### Nó là gì

Render Loop là phần vòng lặp chịu trách nhiệm render frame: collect visible object, prepare draw data, submit draw call và present frame lên màn hình.

### Nó không phải là gì

Render Loop không giống toàn bộ game loop. Game loop có input, simulation, physics, AI và audio; render loop tập trung vào phần tạo frame hình ảnh.

## Core Mechanism / Cơ chế lõi

Mỗi frame, engine xác định camera/view, culling object không thấy, sort/batch render items, set material/shader state, submit draw calls và swap/present buffer.

## Project Role / Vai trò trong dự án

Dùng node này khi debug FPS thấp, frame pacing, object không render, camera/culling sai, draw call cao hoặc khác biệt render giữa editor và build.

## Output / Artifact nên có

- Frame/render profiler capture
- Camera/culling setup
- Draw call/batch breakdown
- CPU/GPU frame time
- Render pipeline/platform note

## Decision Checklist / Câu hỏi kiểm tra

- Bottleneck nằm ở CPU render submit hay GPU?
- Camera/culling có loại nhầm object không?
- Draw call/material state có quá nhiều không?
- Frame pacing có ổn định không?
- Render behavior có khác giữa platform không?

## Failure Modes / Cách nó gây lỗi

- Culling sai làm object biến mất.
- Draw call quá nhiều làm CPU render bottleneck.
- Shader/material đắt làm GPU bottleneck.
- Update logic bị đặt nhầm vào render path.
- VSync/frame pacing làm cảm giác giật dù FPS trung bình ổn.

## Khi nào chưa cần hoặc dễ over-engineer

- Game nhỏ FPS ổn thì chưa cần tối ưu render loop sâu.
- Không nên tối ưu render nếu profiler cho thấy bottleneck nằm ở simulation/network.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Game Loop]] vì render loop là một phần của game loop.
- [[Draw Call]] vì render loop submit draw call.
- [[Shader]] vì shader/material quyết định GPU cost trong render.
- [[Performance Optimization]] vì render loop ảnh hưởng frame time.

## Liên quan rộng

- Frame rendering
- Culling
- Frame pacing

## Keywords / Từ khóa tìm kiếm

- Render Loop
- rendering loop
- frame rendering
- draw call submission
- culling
- frame pacing
- render loop debugging

## Source trace

- Game Programming Patterns
- Unity documentation
- Unreal Engine documentation
