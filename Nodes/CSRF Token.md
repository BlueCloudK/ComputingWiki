# CSRF Token

Aliases: anti-CSRF token, token chống CSRF

Type: Security

## Context / Ngữ cảnh

CSRF Token xuất hiện khi request state-changing cần chứng minh đến từ UI hợp lệ chứ không phải site khác ép browser gửi.

## Boundary / Ranh giới

### Nó là gì

CSRF Token là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của CSRF Token là token generation, validation, SameSite cookie và per-session/per-request scope.

## Project Role / Vai trò trong dự án

CSRF Token giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- CSRF Token decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới CSRF Token
- Failure note ghi rõ CSRF Token ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- CSRF Token đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của CSRF Token không?
- Khi CSRF Token fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của CSRF Token làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên CSRF Token nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu CSRF Token nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh CSRF Token trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Threat modeling
- Backend review
- Frontend architecture
- Browser debugging
- User experience

## Keywords / Từ khóa tìm kiếm

- CSRF Token
- anti-CSRF token
- token chống CSRF
- csrf token debugging
- csrf token design
- security review
- kiểm tra bảo mật
- web development
- frontend debugging
- phát triển web

## Source trace

- OWASP CSRF Prevention Cheat Sheet
