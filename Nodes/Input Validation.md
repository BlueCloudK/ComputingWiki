# Input Validation

Aliases: validate untrusted input, kiểm tra input

## Dùng trong dự án để làm gì

Input Validation giúp kiểm tra phần mềm, tài liệu hoặc thay đổi kỹ thuật trước khi chúng gây lỗi thật trong dự án. Khi team sửa code, refactor, release hoặc tích hợp module, node này giúp chọn đúng mức kiểm tra và biết cần nhìn vào tín hiệu nào.

## Khi nào cần quan tâm

- Chuẩn bị merge hoặc release thay đổi
- Bug cũ quay lại hoặc hành vi mới chưa chắc đúng
- Cần chứng minh một module/luồng đã được kiểm tra

## Lỗi / rủi ro thường gặp

- Test chỉ kiểm tra happy path nên bỏ sót lỗi biên
- Mock quá nhiều làm test xa hành vi thật
- Thiếu regression khiến sửa một chỗ vỡ chỗ khác

## Gồm những gì

- [[Validation]]
- [[XSS]]
- [[SQL Injection]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- OWASP Input Validation Cheat Sheet
