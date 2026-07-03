# Security

Aliases: application security, software security, cybersecurity, bảo mật

Type: Security

## Bản chất

Security liên quan tới bảo vệ asset, identity, permission, input, secret hoặc boundary khỏi misuse. Trọng tâm là attack surface và impact khi fail, không chỉ là thêm một bước check cho có. Nó nối với các phần liên quan như [[Authentication]], [[Authorization]], [[Secret]].

## Dùng trong dự án để làm gì

Security là MOC để đi từ vùng kiến thức lớn xuống các node có thể dùng trong dự án. Nó không thay node chi tiết; nhiệm vụ của nó là gom các quyết định, artifact, checklist và rủi ro liên quan để bạn không đọc rời rạc.

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

- [[Authentication]]
- [[Authorization]]
- [[Secret]]
- [[Input Validation]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- OWASP Map
- SWEBOK Map
- CC2020 Map
