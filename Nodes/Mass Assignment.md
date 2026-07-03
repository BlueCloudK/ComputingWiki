# Mass Assignment

Aliases: Mass Assignment, mass assignment, over-posting, gán trường ngoài ý muốn

Type: Security Attack Pattern

## Context / Ngữ cảnh

Mass Assignment xuất hiện khi review hoặc vận hành hệ thống cần nhận diện binding input tự động cho phép client sửa field không nên được phép sửa.

## Boundary / Ranh giới

### Nó là gì

Mass Assignment là khái niệm bảo mật dùng để đặt tên attack path, control hoặc failure mode khi thiết kế và review hệ thống.

### Nó không phải là gì

Nó không phải hướng dẫn khai thác từng bước; mục tiêu của node là giúp phòng thủ, review, test và giảm rủi ro.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu binding input tự động cho phép client sửa field không nên được phép sửa, boundary nào bị vượt, asset nào bị ảnh hưởng, và control nào phát hiện hoặc chặn được.

## Project Role / Vai trò trong dự án

Mass Assignment giúp team viết requirement bảo mật, review API/code/config, tạo test regression và chuẩn bị monitoring hoặc incident response.

## Output / Artifact nên có

- Threat note hoặc abuse case cho Mass Assignment
- Control/test/checklist phòng thủ tương ứng
- Log/alert signal nếu attack path có thể xảy ra trong production

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào bị ảnh hưởng nếu Mass Assignment xảy ra?
- Trust boundary hoặc permission boundary nào bị vượt?
- Control hiện tại chặn, phát hiện và audit attack path này ở đâu?

## Failure Modes / Cách nó gây lỗi

- Chỉ kiểm tra happy path nên bỏ sót Mass Assignment
- Control đặt ở frontend hoặc layer sai nên attacker bypass được
- Thiếu log/audit làm incident không truy được user, object hoặc request liên quan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony nặng cho Mass Assignment nếu feature không có asset nhạy cảm hoặc exposure công khai
- Dễ over-engineer nếu thêm tool/control mà không map với asset, boundary và likelihood thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Request Validation]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Mass Assignment
- [[Authorization]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Mass Assignment

## Liên quan rộng

- Application security
- Threat modeling
- Security testing

## Keywords / Từ khóa tìm kiếm

- Mass Assignment
- mass assignment
- over-posting
- gán trường ngoài ý muốn
- mass
- assignment

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
