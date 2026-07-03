# Request

Aliases: API request, yêu cầu API

Type: API / Integration

## Bản chất

Request nằm ở boundary nơi client, backend, service hoặc third-party phải hiểu nhau bằng contract. Vấn đề chính không chỉ là gọi được, mà là request/response, validation, error format và compatibility có ổn định không. Nó nối với các phần liên quan như [[Validation]], [[Response]].

## Dùng trong dự án để làm gì

Request quyết định cách các phần của hệ thống tích hợp, đổi version và debug lỗi mismatch. Trong dự án, nó giúp chốt contract trước khi nhiều team/client phụ thuộc vào nhau.

## Khi nào cần quan tâm

- Thiết kế hoặc thay đổi request/response giữa client và server
- Client/server hiểu khác field, status code hoặc error format
- Cần giữ backward compatibility cho consumer cũ
- Tích hợp third-party, webhook, REST/RPC hoặc service nội bộ

## Output / artifact nên có

- API contract hoặc integration decision ghi rõ request/response/error
- Validation rule và compatibility/versioning note
- Test contract hoặc integration test cho path quan trọng

## Checklist kiểm tra

- Request/response có schema và required/optional field rõ chưa?
- Error format có thống nhất và đủ debug không?
- Validation xảy ra ở đâu và message trả về thế nào?
- Change này có breaking với consumer hiện tại không?
- Có test cho mismatch dữ liệu, auth và timeout không?

## Lỗi / rủi ro thường gặp

- Client/server mismatch làm lỗi chỉ xuất hiện khi tích hợp
- Error format không chuẩn khiến frontend và log khó debug
- Breaking change không version làm consumer cũ hỏng
- Validation thiếu khiến dữ liệu bẩn đi sâu vào hệ thống

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần contract quá nặng cho prototype một client một server
- Dễ over-engineer nếu versioning phức tạp khi chưa có consumer ổn định

## Gồm những gì

- [[Validation]]
- [[Response]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- API and Integration
