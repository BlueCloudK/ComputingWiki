# Dependency Confusion

Aliases: Dependency Confusion, dependency confusion, package confusion, nhầm dependency

Type: Security Attack Pattern

## Context / Ngữ cảnh

Dependency Confusion xuất hiện khi review hoặc vận hành hệ thống cần nhận diện package manager cài nhầm package public độc hại thay vì internal package.

## Boundary / Ranh giới

### Nó là gì

Dependency Confusion là khái niệm bảo mật dùng để đặt tên attack path, control hoặc failure mode khi thiết kế và review hệ thống.

### Nó không phải là gì

Nó không phải hướng dẫn khai thác từng bước; mục tiêu của node là giúp phòng thủ, review, test và giảm rủi ro.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu package manager cài nhầm package public độc hại thay vì internal package, boundary nào bị vượt, asset nào bị ảnh hưởng, và control nào phát hiện hoặc chặn được.

## Project Role / Vai trò trong dự án

Dependency Confusion giúp team viết requirement bảo mật, review API/code/config, tạo test regression và chuẩn bị monitoring hoặc incident response.

## Output / Artifact nên có

- Threat note hoặc abuse case cho Dependency Confusion
- Control/test/checklist phòng thủ tương ứng
- Log/alert signal nếu attack path có thể xảy ra trong production

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào bị ảnh hưởng nếu Dependency Confusion xảy ra?
- Trust boundary hoặc permission boundary nào bị vượt?
- Control hiện tại chặn, phát hiện và audit attack path này ở đâu?

## Failure Modes / Cách nó gây lỗi

- Chỉ kiểm tra happy path nên bỏ sót Dependency Confusion
- Control đặt ở frontend hoặc layer sai nên attacker bypass được
- Thiếu log/audit làm incident không truy được user, object hoặc request liên quan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony nặng cho Dependency Confusion nếu feature không có asset nhạy cảm hoặc exposure công khai
- Dễ over-engineer nếu thêm tool/control mà không map với asset, boundary và likelihood thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Supply Chain Security]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Dependency Confusion
- [[Package Manager]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Dependency Confusion

## Liên quan rộng

- Application security
- Threat modeling
- Security testing

## Keywords / Từ khóa tìm kiếm

- Dependency Confusion
- dependency confusion
- package confusion
- nhầm dependency
- dependency
- confusion

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
