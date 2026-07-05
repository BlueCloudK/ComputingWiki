# Shader

Aliases: Shader

Type: Game Development

## Context / Ngữ cảnh

Shader xuất hiện khi game/rendering cần quyết định cách surface, sprite, particle, post-process hoặc UI được GPU vẽ ra màn hình.

## Boundary / Ranh giới

### Nó là gì

Shader là chương trình chạy trên GPU để xử lý vertex, fragment/pixel hoặc compute data, quyết định màu sắc, ánh sáng, texture, hiệu ứng và render behavior.

### Nó không phải là gì

Shader không phải material hoàn chỉnh. Material thường là cấu hình dùng shader kèm texture, parameter và render state.

## Core Mechanism / Cơ chế lõi

Renderer chọn shader/material, gửi mesh/texture/uniform/buffer cho GPU. Shader chạy theo pipeline để transform vertex, sample texture, tính lighting/effect và xuất pixel hoặc data.

## Project Role / Vai trò trong dự án

Dùng node này khi debug object tím/mất material, hiệu ứng sai, shader compile fail, GPU bottleneck, draw call state hoặc khác biệt giữa platform.

## Output / Artifact nên có

- Shader file/graph
- Material parameter list
- Target render pipeline/platform
- Compile variant note
- GPU profiler/checklist nếu performance quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Shader chạy trong render pipeline nào?
- Material parameter có đúng không?
- Shader variant có bị strip/missing không?
- Bottleneck nằm ở fill-rate, texture sample hay math?
- Platform target có hỗ trợ feature shader này không?

## Failure Modes / Cách nó gây lỗi

- Shader compile fail trên platform cụ thể.
- Material thiếu texture/parameter làm render sai.
- Quá nhiều variant làm build nặng.
- Shader quá đắt làm GPU frame time cao.
- Render pipeline đổi làm shader không tương thích.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype gameplay có thể dùng material/shader mặc định trước.
- Không nên viết shader tùy biến nếu effect chuẩn của engine đủ dùng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Draw Call]] vì shader/material state ảnh hưởng batching và draw call.
- [[Sprite]] vì sprite có thể dùng shader/material riêng.
- [[Performance Optimization]] vì shader cost ảnh hưởng GPU frame time.
- [[Asset Pipeline]] vì shader/material là asset cần import/build đúng.

## Liên quan rộng

- GPU pipeline
- Material
- Lighting
- Post-processing

## Keywords / Từ khóa tìm kiếm

- Shader
- shader
- GPU shader
- material shader
- shader variant
- shader compile
- shader debugging

## Source trace

- Unity documentation
- Unreal Engine documentation
- Godot documentation
