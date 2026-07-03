# API Contract

Aliases: request/response contract, hợp đồng API

Type: API / Integration

## Bản chất

API Contract là thỏa thuận kỹ thuật giữa producer và consumer về endpoint, request, response, error, validation và compatibility. Nó không chỉ là mô tả field; nó quyết định client/server có thể phát triển độc lập mà không phá nhau hay không. Contract càng nhiều consumer thì càng cần rõ versioning và backward compatibility.

## Dùng trong dự án để làm gì

API Contract được dùng để chốt dữ liệu vào/ra, status/error format, rule validate và test tích hợp. Trong dự án, nó là tài liệu/nguồn sự thật để frontend, backend, service khác hoặc third-party không hiểu khác nhau khi implement.

## Khi nào cần quan tâm

- Thiết kế hoặc thay đổi request/response giữa client và server
- Client/server hiểu khác field, status code hoặc error format
- Cần giữ backward compatibility cho consumer cũ
- Tích hợp third-party, webhook, REST/RPC hoặc service nội bộ

## Output / artifact nên có

- API contract hoặc integration decision ghi rõ request/response/error
- Validation rule và compatibility/versioning note
- Contract test hoặc integration test cho path quan trọng

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

- [[Request]]
- [[Response]]
- [[Validation]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- API and Integration / Requirements Engineering Map
