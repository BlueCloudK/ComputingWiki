# Security

Aliases: application security, software security, cybersecurity, bảo mật

Type: Security

## Context / Ngữ cảnh

Security xuất hiện ở nơi hệ thống có asset cần bảo vệ: identity, permission, secret, dữ liệu nhạy cảm, input công khai hoặc boundary với third-party.

## Boundary / Ranh giới

### Nó là gì

Security là control hoặc vùng kiến thức giúp giảm khả năng misuse và giảm impact khi control fail.

### Nó không phải là gì

Nó không phải checkbox thêm vào cuối dự án; nếu không map với asset và attack surface thì control dễ sai chỗ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là asset + attack surface + control + audit. Cần biết bảo vệ gì, ai có thể tấn công/lạm dụng, chặn ở đâu, và log thế nào để điều tra.

## Project Role / Vai trò trong dự án

Security là MOC điều hướng: dùng để đi từ vùng lớn xuống node cụ thể, không thay thế node chi tiết. Khi review graph, trang này giúp chọn đúng nhánh cần đọc và tránh link rộng làm rối.

## Output / Artifact nên có

- Security checklist cho asset và attack surface liên quan
- Permission/auth/input validation rule rõ ràng
- Audit/logging decision cho hành động nhạy cảm

## Decision Checklist / Câu hỏi kiểm tra

- Asset nào cần bảo vệ và ai có quyền truy cập?
- Attack surface chính nằm ở input, auth, secret hay dependency?
- Permission được enforce ở tầng nào và có test chưa?
- Log có đủ audit nhưng không lộ secret/PII không?
- Nếu control này fail thì impact tới user/system là gì?

## Failure Modes / Cách nó gây lỗi

- Tin tưởng input hoặc token quá mức
- Authorization bị kiểm tra thiếu ở backend
- Secret/PII lọt vào log hoặc response
- Failure mode trả lỗi quá chi tiết cho attacker

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần security ceremony nặng cho dữ liệu không nhạy trong prototype nội bộ
- Dễ over-engineer nếu thêm nhiều control nhưng không map với asset/attack surface thật

## Gồm những gì

- [[Authentication]]
- [[Authorization]]
- [[Secret]]
- [[Input Validation]]
- [[API Security]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Application security
- Backend
- Audit
- Risk management

## Source trace

- OWASP Map
- SWEBOK Map
- CC2020 Map
