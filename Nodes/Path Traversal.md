# Path Traversal

Aliases: Directory Traversal, traversal path

Type: Security

## Context / Ngữ cảnh

Path Traversal xuất hiện khi input path cho phép đọc/ghi file ngoài thư mục cho phép.

## Boundary / Ranh giới

### Nó là gì

Path Traversal là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Path Traversal là path normalization, base directory enforcement, allowlist và file permission.

## Project Role / Vai trò trong dự án

Path Traversal giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- Path Traversal decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới Path Traversal
- Failure note ghi rõ Path Traversal ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- Path Traversal đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của Path Traversal không?
- Khi Path Traversal fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của Path Traversal làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên Path Traversal nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu Path Traversal nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh Path Traversal trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Threat modeling
- Backend review

## Keywords / Từ khóa tìm kiếm

- Path Traversal
- Directory Traversal
- traversal path
- path traversal debugging
- path traversal design
- security review
- kiểm tra bảo mật

## Source trace

- OWASP Path Traversal
