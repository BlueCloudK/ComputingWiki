# Content Type Validation

Aliases: Content Type Validation, content-type validation, validate MIME, kiểm tra loại file

Type: Security Attack Pattern

## Context / Ngữ cảnh

Content Type Validation xuất hiện khi review hoặc vận hành hệ thống cần nhận diện kiểm tra content type thật và expected behavior của uploaded/served file.

## Boundary / Ranh giới

### Nó là gì

Content Type Validation là khái niệm bảo mật dùng để đặt tên attack path, control hoặc failure mode khi thiết kế và review hệ thống.

### Nó không phải là gì

Nó không phải hướng dẫn khai thác từng bước; mục tiêu của node là giúp phòng thủ, review, test và giảm rủi ro.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu kiểm tra content type thật và expected behavior của uploaded/served file, boundary nào bị vượt, asset nào bị ảnh hưởng, và control nào phát hiện hoặc chặn được.

## Project Role / Vai trò trong dự án

Content Type Validation giúp team viết requirement bảo mật, review API/code/config, tạo test regression và chuẩn bị monitoring hoặc incident response.

## Output / Artifact nên có

- Threat note hoặc abuse case cho Content Type Validation
- Control/test/checklist phòng thủ tương ứng
- Log/alert signal nếu attack path có thể xảy ra trong production

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào bị ảnh hưởng nếu Content Type Validation xảy ra?
- Trust boundary hoặc permission boundary nào bị vượt?
- Control hiện tại chặn, phát hiện và audit attack path này ở đâu?

## Failure Modes / Cách nó gây lỗi

- Chỉ kiểm tra happy path nên bỏ sót Content Type Validation
- Control đặt ở frontend hoặc layer sai nên attacker bypass được
- Thiếu log/audit làm incident không truy được user, object hoặc request liên quan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony nặng cho Content Type Validation nếu feature không có asset nhạy cảm hoặc exposure công khai
- Dễ over-engineer nếu thêm tool/control mà không map với asset, boundary và likelihood thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[File Upload Security]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Content Type Validation
- [[MIME Sniffing]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Content Type Validation

## Liên quan rộng

- Application security
- Threat modeling
- Security testing

## Keywords / Từ khóa tìm kiếm

- Content Type Validation
- content-type validation
- validate MIME
- kiểm tra loại file
- content
- type
- validation

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
