# Horizontal Privilege Escalation

Aliases: Horizontal Privilege Escalation, horizontal privilege escalation, leo thang ngang, truy cập tài khoản khác

Type: Security Attack Pattern

## Context / Ngữ cảnh

Horizontal Privilege Escalation xuất hiện khi review hoặc vận hành hệ thống cần nhận diện user truy cập resource của user khác ở cùng mức quyền.

## Boundary / Ranh giới

### Nó là gì

Horizontal Privilege Escalation là khái niệm bảo mật dùng để đặt tên attack path, control hoặc failure mode khi thiết kế và review hệ thống.

### Nó không phải là gì

Nó không phải hướng dẫn khai thác từng bước; mục tiêu của node là giúp phòng thủ, review, test và giảm rủi ro.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu user truy cập resource của user khác ở cùng mức quyền, boundary nào bị vượt, asset nào bị ảnh hưởng, và control nào phát hiện hoặc chặn được.

## Project Role / Vai trò trong dự án

Horizontal Privilege Escalation giúp team viết requirement bảo mật, review API/code/config, tạo test regression và chuẩn bị monitoring hoặc incident response.

## Output / Artifact nên có

- Threat note hoặc abuse case cho Horizontal Privilege Escalation
- Control/test/checklist phòng thủ tương ứng
- Log/alert signal nếu attack path có thể xảy ra trong production

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào bị ảnh hưởng nếu Horizontal Privilege Escalation xảy ra?
- Trust boundary hoặc permission boundary nào bị vượt?
- Control hiện tại chặn, phát hiện và audit attack path này ở đâu?

## Failure Modes / Cách nó gây lỗi

- Chỉ kiểm tra happy path nên bỏ sót Horizontal Privilege Escalation
- Control đặt ở frontend hoặc layer sai nên attacker bypass được
- Thiếu log/audit làm incident không truy được user, object hoặc request liên quan

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ceremony nặng cho Horizontal Privilege Escalation nếu feature không có asset nhạy cảm hoặc exposure công khai
- Dễ over-engineer nếu thêm tool/control mà không map với asset, boundary và likelihood thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Broken Access Control]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Horizontal Privilege Escalation
- [[IDOR]] vì liên quan trực tiếp tới cách phòng thủ hoặc nhận diện Horizontal Privilege Escalation

## Liên quan rộng

- Application security
- Threat modeling
- Security testing

## Keywords / Từ khóa tìm kiếm

- Horizontal Privilege Escalation
- horizontal privilege escalation
- leo thang ngang
- truy cập tài khoản khác
- horizontal
- privilege
- escalation

## Source trace

- OWASP Top 10
- OWASP Cheat Sheet Series
- OWASP Web Security Testing Guide
- NIST Secure Software Development Framework
