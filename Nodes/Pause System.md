# Pause System

Aliases: Pause System, game pause system

Type: Game Development

## Context / Ngữ cảnh

Pause System xuất hiện khi game cần tạm dừng gameplay nhưng vẫn giữ UI, menu, audio, input hoặc một số animation hoạt động theo rule riêng.

## Boundary / Ranh giới

### Nó là gì

Pause System là cơ chế kiểm soát trạng thái paused/unpaused của game, quyết định system nào dừng, system nào vẫn chạy và input nào còn được nhận.

### Nó không phải là gì

Pause System không chỉ là set time scale về 0. Một số system như pause menu, UI animation, network, audio hoặc cutscene có thể cần behavior riêng.

## Core Mechanism / Cơ chế lõi

Game có pause state trung tâm. Gameplay update/physics/AI/timer kiểm tra state hoặc time source phù hợp; UI/input/audio dùng rule riêng để cho phép mở menu, resume hoặc quit.

## Project Role / Vai trò trong dự án

Dùng node này khi debug game vẫn chạy khi pause, UI không nhận input, timer/cooldown sai, audio không dừng hoặc resume bị lệch state.

## Output / Artifact nên có

- Pause state diagram
- System behavior table: pause/resume/ignore
- Input routing rule
- Time source rule
- Test checklist cho pause/resume

## Decision Checklist / Câu hỏi kiểm tra

- System nào dừng khi pause?
- System nào vẫn chạy khi pause?
- Input nào còn nhận?
- Timer dùng scaled hay unscaled time?
- Pause có được save/load hoặc multiplayer support không?

## Failure Modes / Cách nó gây lỗi

- Gameplay dừng nhưng timer/cooldown vẫn chạy.
- Pause menu không nhận input vì input cũng bị chặn.
- Physics/AI vẫn update khi pause.
- Audio state không resume đúng.
- Nhiều source pause/resume làm state conflict.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype chưa có menu có thể dùng pause tối giản.
- Không nên tạo pause framework phức tạp nếu chỉ cần stop/resume gameplay cơ bản.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Game Loop]] vì pause kiểm soát update loop.
- [[HUD]] vì pause menu/HUD là UI liên quan trực tiếp.
- [[Finite State AI]] vì AI thường phải dừng hoặc đổi state khi pause.
- [[State Management]] vì pause là global gameplay state cần quản lý rõ.

## Liên quan rộng

- Time scale
- Pause menu
- Gameplay state

## Keywords / Từ khóa tìm kiếm

- Pause System
- game pause system
- time scale
- unscaled time
- pause menu
- gameplay pause
- pause system debugging

## Source trace

- Game Programming Patterns
- Unity documentation
- Godot documentation
