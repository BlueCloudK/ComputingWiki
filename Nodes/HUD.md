# HUD

Aliases: HUD, Heads-Up Display

Type: Game Development

## Context / Ngữ cảnh

HUD xuất hiện khi game cần hiển thị thông tin trạng thái trực tiếp trên màn hình trong lúc chơi.

## Boundary / Ranh giới

### Nó là gì

HUD là lớp UI gameplay hiển thị thông tin như máu, điểm, đạn, minimap, nhiệm vụ hoặc cooldown.

### Nó không phải là gì

HUD không phải toàn bộ menu UI. Menu, inventory hoặc setting screen có thể là UI khác ngoài gameplay HUD.

## Core Mechanism / Cơ chế lõi

Gameplay system cập nhật state, HUD đọc hoặc nhận event rồi render thông tin cần thiết lên UI layer. HUD cần rõ data source, update frequency và priority hiển thị.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế UI gameplay, debug điểm/máu hiển thị sai, hoặc tối ưu overlay trong game.

## Output / Artifact nên có

- HUD layout mockup
- State/data source map
- Update rule cho từng indicator
- Test checklist trong gameplay chính

## Decision Checklist / Câu hỏi kiểm tra

- HUD cần hiển thị thông tin nào?
- Data đến từ system nào?
- Thông tin nào ưu tiên cao nhất?
- HUD có che gameplay không?

## Failure Modes / Cách nó gây lỗi

- HUD hiển thị state cũ.
- HUD quá nhiều thông tin làm rối màn hình.
- UI update quá thường gây performance cost.
- Data source không rõ làm debug khó.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype gameplay rất sớm có thể dùng HUD tạm.
- Không nên polish HUD trước khi core loop ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Game Loop]] vì HUD thường cập nhật theo state gameplay.
- [[UI]] vì HUD là lớp giao diện trong game.
- [[Performance Optimization]] vì HUD update/render có thể ảnh hưởng frame time.

## Liên quan rộng

- Gameplay UI
- Game feedback
- Player information

## Keywords / Từ khóa tìm kiếm

- HUD
- Heads-Up Display
- gameplay UI
- health bar
- score UI
- minimap
- HUD debugging

## Source trace

- Game Programming Patterns
- Unity documentation
