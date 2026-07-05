# Sprite

Aliases: Sprite

Type: Game Development

## Context / Ngữ cảnh

Sprite xuất hiện khi game hoặc UI 2D cần hiển thị hình ảnh phẳng như nhân vật, vật phẩm, icon, effect hoặc tile.

## Boundary / Ranh giới

### Nó là gì

Sprite là graphic 2D được render trong game engine, thường lấy từ texture hoặc sprite atlas.

### Nó không phải là gì

Sprite không phải toàn bộ animation system. Animation có thể dùng nhiều sprite frame hoặc transform riêng.

## Core Mechanism / Cơ chế lõi

Engine lấy texture region, material/shader và transform để render sprite lên scene/canvas. Sprite có thể nằm trong atlas để giảm draw call và tối ưu memory.

## Project Role / Vai trò trong dự án

Dùng node này khi debug asset 2D, render order, animation frame, sprite atlas hoặc performance UI/game 2D.

## Output / Artifact nên có

- Sprite asset
- Atlas/import setting
- Pixel density/scale note
- Render order/layer note
- Animation frame note nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Sprite dùng texture nào?
- Scale/pixel density có đúng không?
- Render layer/order có đúng không?
- Có cần atlas để tối ưu không?

## Failure Modes / Cách nó gây lỗi

- Sprite bị mờ do import/scale sai.
- Render order sai làm bị che.
- Atlas packing sai làm cắt hình lệch.
- Quá nhiều sprite riêng làm tăng draw call.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype có thể dùng placeholder sprite.
- Không nên tối ưu atlas quá sớm nếu asset còn thay đổi mạnh.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Shader]] vì sprite có thể dùng shader/material để render.
- [[Asset Pipeline]] vì sprite cần import/pack/config đúng.
- [[Performance Optimization]] vì số lượng sprite/draw call ảnh hưởng frame time.

## Liên quan rộng

- 2D rendering
- Game asset
- Animation frame

## Keywords / Từ khóa tìm kiếm

- Sprite
- 2D sprite
- sprite atlas
- render order
- draw call
- sprite debugging

## Source trace

- Unity documentation
- Godot documentation
