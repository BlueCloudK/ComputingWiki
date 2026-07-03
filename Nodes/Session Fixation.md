# Session Fixation

Aliases: session fixation attack, cố định phiên

Type: Security

## Context / Ngữ cảnh

Session Fixation xuất hiện khi attacker ép nạn nhân dùng session id do attacker biết trước để chiếm phiên sau login.

## Boundary / Ranh giới

### Nó là gì

Session Fixation là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Session Fixation là session regeneration, cookie flags, login boundary và invalidation.

## Project Role / Vai trò trong dự án

Session Fixation giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Session Fixation decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Session Fixation
- Failure note ghi rõ Session Fixation ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Session Fixation đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Session Fixation không?
- Khi Session Fixation fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Session Fixation làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Session Fixation nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Session Fixation nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Session Fixation trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Threat modeling
- Backend review

## Keywords / Từ khóa tìm kiếm

- Session Fixation
- session fixation attack
- cố định phiên
- session fixation debugging
- session fixation design
- security review
- kiểm tra bảo mật

## Source trace

- OWASP Session Management Cheat Sheet
