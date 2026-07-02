# JSON

Aliases: JavaScript Object Notation, định dạng JSON

## Dùng trong dự án để làm gì

JSON ảnh hưởng tới cách hệ thống lưu, đọc, trao đổi và kiểm soát dữ liệu. Trong dự án, nó thường xuất hiện ở database design, API payload, migration, transaction, reporting hoặc khi debug lỗi dữ liệu sai lệch.

## Khi nào cần quan tâm

- Thiết kế schema, payload hoặc data model
- Dữ liệu bị sai, thiếu, trùng hoặc khó migrate
- Tích hợp hệ thống cần thống nhất format và contract

## Lỗi / rủi ro thường gặp

- Schema và code hiểu khác nhau về field/type
- Migration hoặc transaction làm mất/tạo sai dữ liệu
- Format thay đổi mà consumer không được cập nhật

## Gồm những gì

- Chưa tách nhánh

## Liên quan

- [[API Contract]]

## Source trace

- Data Intensive Applications Map / Ch04
