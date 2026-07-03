# Distributed Denial of Service

Aliases: Distributed Denial of Service, DDoS, distributed denial of service, DDoS attack

Type: Security Attack Pattern

## Context / Ngữ cảnh

Distributed Denial of Service xuất hiện khi review hoặc vận hành hệ thống cần nhận diện DoS từ nhiều nguồn làm network/app/backend quá tải.

## Boundary / Ranh giới

### Nó là gì

Distributed Denial of Service là khái niệm bảo mật dùng để đặt tên attack path, control hoặc failure mode khi thiết kế và review hệ thống.

### Nó không phải là gì

Nó không phải hướng dẫn khai thác từng bước; mục tiêu của node là giúp phòng thủ, review, test và giảm rủi ro.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu DoS từ nhiều nguồn làm network/app/backend quá tải, boundary nào bị vượt, asset nào bị ảnh hưởng, và control nào phát hiện hoặc chặn được.

## Project Role / Vai trò trong dự án

Distributed Denial of Service giúp team viết requirement bảo mật, review API/code/config, tạo test regression và chuẩn bị monitoring hoặc incident response.

## Output / Artifact nên có

- Threat note hoặc abuse case cho Distributed Denial of Service
- Control/test/checklist phòng thủ tương ứng
- Log/alert signal nếu attack path có thể xảy ra trong production

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào bị ảnh hưởng nếu Distributed Denial of Service xảy ra?
- Trust boundary hoặc permission boundary nào bị vượt?
- Control hiện tại chặn, phát hiện và audit attack path này ở đâu?

## Failure Modes / Cách nó gây lỗi

- Chỉ kiểm tra happy path nên bỏ sót Distributed Denial of Service
- Control đặt ở frontend hoặc layer sai nên attacker bypass được
- Thiếu log/audit làm incident không truy được user, object hoặc request liên quan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony nặng cho Distributed Denial of Service nếu feature không có asset nhạy cảm hoặc exposure công khai
- Dễ over-engineer nếu thêm tool/control mà không map với asset, boundary và likelihood thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Denial of Service]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Distributed Denial of Service
- [[Rate Limiting]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Distributed Denial of Service

## Liên quan rộng

- Application security
- Threat modeling
- Security testing

## Keywords / Từ khóa tìm kiếm

- Distributed Denial of Service
- DDoS
- distributed denial of service
- DDoS attack
- distributed
- denial
- service

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
