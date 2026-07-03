# API and Integration

Aliases: API, integration, API và tích hợp

Type: API / Integration

## Bản chất

API and Integration là vùng boundary nơi frontend, backend, service nội bộ và third-party phải hiểu cùng contract. Trọng tâm là request/response, validation, error format, auth boundary và compatibility khi một bên thay đổi. MOC này gom các node giúp kiểm soát lỗi tích hợp trước khi chúng thành bug production.

## Dùng trong dự án để làm gì

API and Integration là MOC để đi nhanh tới các node phục vụ thiết kế contract, kiểm tra mismatch và debug integration. Khi làm dự án, dùng trang này để xác định phải tạo contract gì, test gì và rule compatibility nào trước khi nhiều consumer phụ thuộc vào API.

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

- [[API Contract]]
- [[Validation]]
- [[Error Handling]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Data Intensive Applications Map
- Requirements Engineering Map
- Software Modeling and Design Map
