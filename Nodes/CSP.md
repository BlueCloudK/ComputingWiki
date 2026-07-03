# CSP

Aliases: Content Security Policy, chính sách bảo mật nội dung

Type: Security / Web

## Context / Ngữ cảnh

CSP xuất hiện khi browser cần giới hạn nguồn script/style/img để giảm impact của XSS.

## Boundary / Ranh giới

### Nó là gì

CSP là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của CSP là directive, nonce/hash, report-only mode, script-src và violation report.

## Project Role / Vai trò trong dự án

CSP giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- CSP decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới CSP
- Failure note ghi rõ CSP ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- CSP đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của CSP không?
- Khi CSP fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của CSP làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên CSP nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu CSP nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh CSP trước khi có nhu cầu vận hành hoặc học tập rõ

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

- CSP
- Content Security Policy
- chính sách bảo mật nội dung
- csp debugging
- csp design
- security review
- kiểm tra bảo mật
- web development
- frontend debugging
- phát triển web

## Source trace

- MDN CSP; OWASP CSP Cheat Sheet
