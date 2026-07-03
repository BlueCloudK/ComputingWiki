# RCE

Aliases: Remote Code Execution, thực thi mã từ xa

Type: Security

## Context / Ngữ cảnh

RCE xuất hiện khi attacker có thể chạy code hoặc command trên server/runtime nạn nhân.

## Boundary / Ranh giới

### Nó là gì

RCE là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của RCE là unsafe deserialization, command injection, sandbox escape và patch boundary.

## Project Role / Vai trò trong dự án

RCE giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- RCE decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới RCE
- Failure note ghi rõ RCE ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- RCE đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của RCE không?
- Khi RCE fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của RCE làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên RCE nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu RCE nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh RCE trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Threat modeling
- Backend review

## Keywords / Từ khóa tìm kiếm

- RCE
- Remote Code Execution
- thực thi mã từ xa
- rce debugging
- rce design
- security review
- kiểm tra bảo mật

## Source trace

- OWASP Testing Guide
