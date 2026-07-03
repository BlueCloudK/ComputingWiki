# JWT Attack

Aliases: JWT vulnerability, tấn công JWT

Type: Security

## Context / Ngữ cảnh

JWT Attack xuất hiện khi JWT bị dùng sai như bỏ verify signature, trust alg none hoặc validate claim thiếu.

## Boundary / Ranh giới

### Nó là gì

JWT Attack là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của JWT Attack là signature verification, algorithm allowlist, claim validation và key rotation.

## Project Role / Vai trò trong dự án

JWT Attack giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- JWT Attack decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới JWT Attack
- Failure note ghi rõ JWT Attack ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- JWT Attack đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của JWT Attack không?
- Khi JWT Attack fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của JWT Attack làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên JWT Attack nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu JWT Attack nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh JWT Attack trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Threat modeling
- Backend review

## Keywords / Từ khóa tìm kiếm

- JWT Attack
- JWT vulnerability
- tấn công JWT
- jwt attack debugging
- jwt attack design
- security review
- kiểm tra bảo mật

## Source trace

- OWASP JWT Cheat Sheet
