# Finite State AI

Aliases: Finite State AI, FSM AI

Type: Game Development

## Context / Ngữ cảnh

Finite State AI xuất hiện khi game NPC/enemy cần hành vi rõ ràng theo trạng thái như idle, patrol, chase, attack, flee hoặc dead.

## Boundary / Ranh giới

### Nó là gì

Finite State AI là cách mô hình hóa AI game bằng finite state machine: entity ở một state tại một thời điểm và chuyển state theo condition/event.

### Nó không phải là gì

Finite State AI không phải machine learning. Nó là rule-based gameplay logic, dễ kiểm soát nhưng có thể cứng nếu hành vi quá phức tạp.

## Core Mechanism / Cơ chế lõi

Mỗi state có enter/update/exit behavior. Condition như khoảng cách player, line of sight, cooldown, health hoặc event quyết định transition sang state khác.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế enemy AI đơn giản, debug NPC kẹt state, animation/behavior không khớp hoặc cần behavior có thể test thủ công.

## Output / Artifact nên có

- State diagram
- Transition condition list
- Per-state behavior
- Debug current-state display/log
- Test scenario cho state quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- NPC có những state nào?
- Transition nào được ưu tiên nếu nhiều condition cùng đúng?
- State có enter/exit cleanup không?
- Có state nào không thoát được không?
- Animation và gameplay state có đồng bộ không?

## Failure Modes / Cách nó gây lỗi

- Transition condition chồng chéo làm AI nhảy state liên tục.
- Thiếu exit condition làm NPC kẹt.
- State diagram không khớp code thật.
- Animation state và gameplay state lệch nhau.
- FSM phình quá lớn khi hành vi phức tạp.

## Khi nào chưa cần hoặc dễ over-engineer

- NPC chỉ có một hành vi đơn giản có thể dùng script trực tiếp.
- Không nên dùng FSM lớn nếu behavior cần planning/utility phức tạp hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Game Loop]] vì AI state thường update mỗi frame/tick.
- [[Animation State Machine]] vì gameplay state thường cần đồng bộ animation.
- [[Quest System]] vì quest/event có thể kích hoạt state AI.
- [[Debugging]] vì state display/log rất hữu ích khi debug AI.

## Liên quan rộng

- State machine
- Enemy AI
- NPC behavior

## Keywords / Từ khóa tìm kiếm

- Finite State AI
- FSM AI
- finite state machine
- enemy AI
- NPC state
- state transition
- finite state AI debugging

## Source trace

- Game Programming Patterns
- Unity documentation
