# Arbitrary File Read

Aliases: Arbitrary File Read, arbitrary file read, đọc file tùy ý, file disclosure

Type: Security Attack Pattern

## Context / Ngữ cảnh

Arbitrary File Read xuất hiện khi review hoặc vận hành hệ thống cần nhận diện lỗ hổng cho phép đọc file server ngoài intended scope.

## Boundary / Ranh giới

### Nó là gì

Arbitrary File Read là khái niệm bảo mật dùng để đặt tên attack path, control hoặc failure mode khi thiết kế và review hệ thống.

### Nó không phải là gì

Nó không phải hướng dẫn khai thác từng bước; mục tiêu của node là giúp phòng thủ, review, test và giảm rủi ro.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu lỗ hổng cho phép đọc file server ngoài intended scope, boundary nào bị vượt, asset nào bị ảnh hưởng, và control nào phát hiện hoặc chặn được.

## Project Role / Vai trò trong dự án

Arbitrary File Read giúp team viết requirement bảo mật, review API/code/config, tạo test regression và chuẩn bị monitoring hoặc incident response.

## Output / Artifact nên có

- Threat note hoặc abuse case cho Arbitrary File Read
- Control/test/checklist phòng thủ tương ứng
- Log/alert signal nếu attack path có thể xảy ra trong production

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào bị ảnh hưởng nếu Arbitrary File Read xảy ra?
- Trust boundary hoặc permission boundary nào bị vượt?
- Control hiện tại chặn, phát hiện và audit attack path này ở đâu?

## Failure Modes / Cách nó gây lỗi

- Chỉ kiểm tra happy path nên bỏ sót Arbitrary File Read
- Control đặt ở frontend hoặc layer sai nên attacker bypass được
- Thiếu log/audit làm incident không truy được user, object hoặc request liên quan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony nặng cho Arbitrary File Read nếu feature không có asset nhạy cảm hoặc exposure công khai
- Dễ over-engineer nếu thêm tool/control mà không map với asset, boundary và likelihood thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Path Traversal]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Arbitrary File Read
- [[Secret]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Arbitrary File Read

## Liên quan rộng

- Application security
- Threat modeling
- Security testing

## Keywords / Từ khóa tìm kiếm

- Arbitrary File Read
- arbitrary file read
- đọc file tùy ý
- file disclosure
- arbitrary
- file
- read

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
