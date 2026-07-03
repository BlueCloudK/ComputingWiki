# Protection

Aliases: protection, bảo vệ tài nguyên

Type: Security

## Bản chất

Protection liên quan tới bảo vệ asset, identity, permission, input, secret hoặc boundary khỏi misuse. Trọng tâm là attack surface và impact khi fail, không chỉ là thêm một bước check cho có.

## Dùng trong dự án để làm gì

Protection ảnh hưởng tới auth flow, data exposure, logging/audit và cách hệ thống phản ứng khi bị abuse. Trong dự án, nó giúp chặn lỗi bảo mật trước khi biến thành leak, privilege escalation hoặc incident.

## Khi nào cần quan tâm

- Có user input, token, secret, file upload hoặc dữ liệu nhạy cảm
- Thiết kế permission/authentication/authorization
- API public hoặc boundary giữa service/third-party
- Cần log/audit hành động nhạy cảm

## Output / artifact nên có

- Security checklist cho asset và attack surface liên quan
- Permission/auth/input validation rule rõ ràng
- Audit/logging decision cho hành động nhạy cảm

## Checklist kiểm tra

- Asset nào cần bảo vệ và ai có quyền truy cập?
- Attack surface chính nằm ở input, auth, secret hay dependency?
- Permission được enforce ở tầng nào và có test chưa?
- Log có đủ audit nhưng không lộ secret/PII không?
- Nếu control này fail thì impact tới user/system là gì?

## Lỗi / rủi ro thường gặp

- Tin tưởng input hoặc token quá mức
- Authorization bị kiểm tra thiếu ở backend
- Secret/PII lọt vào log hoặc response
- Failure mode trả lỗi quá chi tiết cho attacker

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần security ceremony nặng cho dữ liệu không nhạy trong prototype nội bộ
- Dễ over-engineer nếu thêm nhiều control nhưng không map với asset/attack surface thật

## Gồm những gì

- Chưa tách nhánh

## Liên quan

- Chưa liên kết thêm

## Source trace

- Operating Systems Map / Ch01.5/security chapter
