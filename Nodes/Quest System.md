# Quest System

Aliases: Quest System, quest system

Type: Game Development

## Context / Ngữ cảnh

Quest System xuất hiện khi game cần quản lý nhiệm vụ, objective, progress, reward, dialogue trigger hoặc world state liên quan tới hành trình người chơi.

## Boundary / Ranh giới

### Nó là gì

Quest System là hệ thống theo dõi quest state, objective, condition, event và reward để biết người chơi đang làm gì, đã hoàn thành gì và mở khóa gì tiếp theo.

### Nó không phải là gì

Quest System không phải chỉ là text hiển thị nhiệm vụ. UI quest log chỉ là một phần; phần lõi là state/progress logic và event integration.

## Core Mechanism / Cơ chế lõi

Quest có state như locked, active, completed, failed. Objective lắng nghe event gameplay như kill, collect, enter area, talk NPC hoặc trigger cutscene, rồi cập nhật progress và phát reward/unlock khi condition đạt.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế mission/quest flow, debug quest không update, reward không phát, save/load quest state hoặc narrative progression.

## Output / Artifact nên có

- Quest state diagram
- Objective/condition list
- Event trigger mapping
- Reward/unlock rule
- Save/load test checklist

## Decision Checklist / Câu hỏi kiểm tra

- Quest có những state nào?
- Objective nghe event nào?
- Progress được lưu ở đâu?
- Reward phát một lần hay lặp được?
- Quest fail/abandon/reset xử lý ra sao?

## Failure Modes / Cách nó gây lỗi

- Event trigger không fire nên quest kẹt.
- Progress không lưu đúng khi load game.
- Reward phát nhiều lần vì thiếu idempotency.
- Quest dependency tạo dead-end.
- UI quest log hiển thị khác state thật.

## Khi nào chưa cần hoặc dễ over-engineer

- Game prototype chưa có progression có thể dùng trigger/script đơn giản.
- Không nên xây quest engine phức tạp nếu game chỉ có vài nhiệm vụ tuyến tính.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Game Loop]] vì quest progress thường cập nhật qua event trong gameplay.
- [[Finite State AI]] vì NPC/AI state có thể bị quest trigger ảnh hưởng.
- [[Save System]] vì quest state cần được lưu/khôi phục.
- [[HUD]] vì objective/progress thường hiển thị cho player.

## Liên quan rộng

- Mission system
- Objective tracking
- Reward flow

## Keywords / Từ khóa tìm kiếm

- Quest System
- quest system
- mission system
- objective tracking
- quest state
- reward trigger
- quest system debugging

## Source trace

- Game Programming Patterns
- Unity documentation
- Unreal Engine documentation
