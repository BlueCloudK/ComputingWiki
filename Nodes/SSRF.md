# SSRF

Aliases: Server-Side Request Forgery, giả mạo request phía server

Type: Security

## Context / Ngữ cảnh

SSRF xuất hiện khi attacker có thể ép server gửi request tới địa chỉ nội bộ hoặc service không nên truy cập.

## Boundary / Ranh giới

### Nó là gì

SSRF là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của SSRF là URL fetch boundary, allowlist, metadata endpoint protection và egress control.

## Project Role / Vai trò trong dự án

SSRF giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- SSRF decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới SSRF
- Failure note ghi rõ SSRF ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- SSRF đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của SSRF không?
- Khi SSRF fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của SSRF làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên SSRF nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu SSRF nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh SSRF trước khi có nhu cầu vận hành hoặc học tập rõ

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

- SSRF
- Server-Side Request Forgery
- giả mạo request phía server
- ssrf debugging
- ssrf design
- security review
- kiểm tra bảo mật
- web development
- frontend debugging
- phát triển web

## Source trace

- OWASP SSRF Prevention Cheat Sheet
