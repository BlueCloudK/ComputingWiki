# Form Validation

Aliases: client validation, server validation, kiểm tra form

Type: Web Development / Backend

## Context / Ngữ cảnh

Form Validation xuất hiện khi input form cần báo lỗi sớm ở UI và bảo vệ backend khỏi dữ liệu sai.

## Boundary / Ranh giới

### Nó là gì

Form Validation là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Form Validation là HTML constraint validation, custom validation, server-side validation và error display.

## Project Role / Vai trò trong dự án

Form Validation giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Form Validation decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Form Validation
- Failure note ghi rõ Form Validation ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Form Validation đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Form Validation không?
- Khi Form Validation fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Form Validation làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Form Validation nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Form Validation nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Form Validation trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Frontend architecture
- Browser debugging
- User experience

## Keywords / Từ khóa tìm kiếm

- Form Validation
- client validation
- server validation
- kiểm tra form
- form validation debugging
- form validation design
- web development
- frontend debugging
- phát triển web

## Source trace

- MDN Constraint validation; OWASP Input Validation
