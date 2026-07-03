# Cookie

Aliases: HTTP cookie, browser cookie, cookie phiên

Type: Backend / Web Security

## Context / Ngữ cảnh

Cookie xuất hiện khi browser cần lưu và tự gửi state nhỏ theo request tới domain phù hợp.

## Boundary / Ranh giới

### Nó là gì

Cookie là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Cookie là Set-Cookie, SameSite, Secure, HttpOnly, expiry và domain/path scope.

## Project Role / Vai trò trong dự án

Cookie giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Cookie decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Cookie
- Failure note ghi rõ Cookie ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Cookie đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Cookie không?
- Khi Cookie fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Cookie làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Cookie nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Cookie nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Cookie trước khi có nhu cầu vận hành hoặc học tập rõ

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

- Cookie
- HTTP cookie
- browser cookie
- cookie phiên
- cookie debugging
- cookie design
- security review
- kiểm tra bảo mật
- web development
- frontend debugging
- phát triển web

## Source trace

- MDN Cookies; RFC 6265
