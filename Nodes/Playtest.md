# Playtest

Aliases: Playtest, playtesting

Type: Game Development

## Context / Ngữ cảnh

Playtest xuất hiện khi game cần kiểm tra trải nghiệm thật của người chơi: fun, difficulty, control, pacing, clarity, bug và onboarding.

## Boundary / Ranh giới

### Nó là gì

Playtest là buổi/tập thử game với người chơi thật hoặc tester để quan sát hành vi, thu feedback và phát hiện vấn đề không lộ ra khi developer tự chơi.

### Nó không phải là gì

Playtest không chỉ là hỏi “game có vui không”. Cần goal, scenario, observation, metric và câu hỏi đúng để tránh feedback mơ hồ.

## Core Mechanism / Cơ chế lõi

Team chuẩn bị build, task/scenario, người chơi mục tiêu và cách ghi nhận. Trong test, quan sát player hành động, ghi điểm kẹt/confuse/frustration, sau đó tổng hợp issue và ưu tiên fix.

## Project Role / Vai trò trong dự án

Dùng node này khi kiểm tra core loop, tutorial, difficulty curve, level design, UI clarity hoặc trước milestone/release.

## Output / Artifact nên có

- Playtest goal
- Test build/version
- Scenario/task list
- Observation notes
- Issue priority and action list

## Decision Checklist / Câu hỏi kiểm tra

- Playtest muốn kiểm tra giả thuyết nào?
- Tester có giống target player không?
- Build có đủ ổn để test đúng thứ cần test không?
- Quan sát behavior hay chỉ hỏi opinion?
- Feedback được chuyển thành action nào?

## Failure Modes / Cách nó gây lỗi

- Test với người không đại diện target player.
- Hỏi dẫn dắt làm feedback lệch.
- Developer giải thích trong lúc test nên che lỗi onboarding.
- Chỉ nghe opinion, không quan sát hành vi.
- Không chốt action sau playtest.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype chưa có core interaction có thể tự test nhanh trước.
- Không nên tổ chức playtest lớn nếu build quá vỡ khiến không test được giả thuyết chính.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Game Build]] vì playtest cần build cụ thể để trace feedback.
- [[Game Loop]] vì core loop là mục tiêu playtest quan trọng.
- [[HUD]] vì UI clarity thường lộ trong playtest.
- [[Regression Test]] vì bug đã fix từ playtest nên có guard nếu lặp lại.

## Liên quan rộng

- User testing
- Game feedback
- Difficulty tuning
- Onboarding

## Keywords / Từ khóa tìm kiếm

- Playtest
- playtesting
- game testing
- player feedback
- usability test
- difficulty tuning
- playtest debugging

## Source trace

- Game Programming Patterns
- Unity documentation
- Game design playtesting references
