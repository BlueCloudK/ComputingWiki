# XSS

Aliases: cross-site scripting, lỗi XSS

## Dùng trong dự án để làm gì

XSS dùng để nhận diện, giảm và kiểm soát rủi ro bảo mật trong hệ thống. Nó thường xuất hiện khi thiết kế auth, API, dữ liệu nhạy cảm, boundary giữa service hoặc lúc review một luồng có thể bị abuse.

## Khi nào cần quan tâm

- Thiết kế auth, permission hoặc xử lý dữ liệu nhạy cảm
- Có input từ user, API công khai hoặc third-party
- Review rủi ro trước khi release

## Lỗi / rủi ro thường gặp

- Tin tưởng input hoặc token quá mức
- Permission/authentication bị hiểu nhầm giữa các tầng
- Log hoặc response làm lộ thông tin nhạy cảm

## Gồm những gì

- [[Input Validation]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- OWASP XSS Prevention Cheat Sheet
