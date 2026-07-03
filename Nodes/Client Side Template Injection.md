# Client Side Template Injection

Aliases: Client Side Template Injection, CSTI, client-side template injection, chèn template phía client

Type: Security Attack Pattern

## Context / Ngữ cảnh

Client Side Template Injection xuất hiện khi review hoặc vận hành hệ thống cần nhận diện template injection trong framework/template phía client.

## Boundary / Ranh giới

### Nó là gì

Client Side Template Injection là khái niệm bảo mật dùng để đặt tên attack path, control hoặc failure mode khi thiết kế và review hệ thống.

### Nó không phải là gì

Nó không phải hướng dẫn khai thác từng bước; mục tiêu của node là giúp phòng thủ, review, test và giảm rủi ro.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu template injection trong framework/template phía client, boundary nào bị vượt, asset nào bị ảnh hưởng, và control nào phát hiện hoặc chặn được.

## Project Role / Vai trò trong dự án

Client Side Template Injection giúp team viết requirement bảo mật, review API/code/config, tạo test regression và chuẩn bị monitoring hoặc incident response.

## Output / Artifact nên có

- Threat note hoặc abuse case cho Client Side Template Injection
- Control/test/checklist phòng thủ tương ứng
- Log/alert signal nếu attack path có thể xảy ra trong production

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào bị ảnh hưởng nếu Client Side Template Injection xảy ra?
- Trust boundary hoặc permission boundary nào bị vượt?
- Control hiện tại chặn, phát hiện và audit attack path này ở đâu?

## Failure Modes / Cách nó gây lỗi

- Chỉ kiểm tra happy path nên bỏ sót Client Side Template Injection
- Control đặt ở frontend hoặc layer sai nên attacker bypass được
- Thiếu log/audit làm incident không truy được user, object hoặc request liên quan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony nặng cho Client Side Template Injection nếu feature không có asset nhạy cảm hoặc exposure công khai
- Dễ over-engineer nếu thêm tool/control mà không map với asset, boundary và likelihood thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Template Injection]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Client Side Template Injection
- [[DOM XSS]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Client Side Template Injection

## Liên quan rộng

- Application security
- Threat modeling
- Security testing

## Keywords / Từ khóa tìm kiếm

- Client Side Template Injection
- CSTI
- client-side template injection
- chèn template phía client
- client
- side
- template
- injection

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
