# API Contract

Aliases: request/response contract, hợp đồng API, interface contract, service contract, hợp đồng giao tiếp API

Type: API / Integration

## Context / Ngữ cảnh

API Contract xuất hiện ở boundary giữa client, frontend, backend, service nội bộ hoặc third-party. Nó làm rõ một bên phải gửi gì, bên kia trả gì, lỗi được biểu diễn thế nào và thay đổi sau này có phá consumer hiện tại không.

## Boundary / Ranh giới

### Nó là gì

API Contract là thỏa thuận kỹ thuật về endpoint/operation: method, path, request schema, response schema, error format, auth requirement, status code, timeout expectation, versioning và compatibility rule. Nó giúp hai bên tích hợp phát triển/test độc lập mà vẫn không lệch hành vi.

### Nó không phải là gì

API Contract không chỉ là URL hoặc function call. Nó cũng không phải tài liệu trang trí sau khi code xong. Nếu contract không nói rõ validation, error, auth, optional/required field và breaking change, integration vẫn dễ vỡ dù endpoint gọi được.

## Core Mechanism / Cơ chế lõi

Contract biến behavior API thành schema và rule kiểm chứng được. Request/response schema định nghĩa shape dữ liệu; validation rule quyết định input sai bị từ chối ra sao; error model cho client biết xử lý lỗi; versioning/backward compatibility bảo vệ consumer khi provider thay đổi.

## Project Role / Vai trò trong dự án

API Contract ảnh hưởng tới API design, frontend/backend handoff, service integration, SDK generation, contract testing và incident debugging. Khi nhiều team/service cùng phát triển, contract là điểm neo để review breaking change và xác định lỗi nằm ở provider hay consumer.

## Output / Artifact nên có

- OpenAPI/spec hoặc contract note ghi rõ request, response, error và auth
- Required/optional field, enum, nullable, default và validation rule
- Status code/error format convention
- Compatibility/versioning note cho thay đổi field/path/behavior
- Contract test hoặc integration test cho consumer/provider quan trọng
- Example request/response cho happy path và failure path

## Decision Checklist / Câu hỏi kiểm tra

- Request/response có schema rõ required/optional/nullable không?
- Error format có thống nhất và đủ thông tin debug cho client không?
- Validation xảy ra ở đâu và trả lỗi theo format nào?
- Field mới có backward compatible với consumer cũ không?
- Có breaking change nào cần versioning hoặc migration period không?
- Auth/scope/permission có nằm trong contract không?
- Có contract test để bắt mismatch trước khi deploy không?

## Failure Modes / Cách nó gây lỗi

- Client/server hiểu khác nhau về optional field làm lỗi chỉ xuất hiện khi tích hợp.
- Error format không chuẩn khiến frontend xử lý sai hoặc không hiển thị được lỗi.
- Breaking change không version làm consumer cũ hỏng sau deploy.
- Validation thiếu hoặc không đồng nhất làm dữ liệu bẩn đi sâu vào hệ thống.
- Contract không mô tả timeout/rate limit khiến consumer retry hoặc gọi sai kỳ vọng.
- Spec không khớp code thật làm tài liệu gây nhiễu thay vì giúp debug.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype một client một server có thể bắt đầu bằng contract nhẹ trong README hoặc test.
- Không nên tạo versioning phức tạp khi chưa có consumer ổn định.
- Không nên để contract quá trừu tượng; contract tốt phải đủ cụ thể để test và debug.

## Gồm những gì

- [[Request]]
- [[Response]]
- [[Validation]]

## Nối mạnh

- [[API Endpoint]] vì mỗi endpoint cần contract request/response/error rõ ràng.
- [[OpenAPI]] vì OpenAPI là artifact phổ biến để mô tả API contract.
- [[API Versioning]] vì contract thay đổi phải giữ compatibility hoặc version hóa.
- [[Integration Test]] vì contract cần được kiểm chứng giữa provider và consumer.

## Liên quan rộng

- Backend
- Frontend
- Third-party integration
- Contract testing
- SDK generation

## Keywords / Từ khóa tìm kiếm

- API Contract
- request response contract
- interface contract
- service contract
- hợp đồng API
- hợp đồng giao tiếp API
- API schema
- OpenAPI contract
- error format
- validation rule
- contract test
- backward compatibility
- breaking change
- frontend backend handoff
- đặc tả request response

## Source trace

- Microsoft REST API Guidelines
- Google API Improvement Proposals
- OpenAPI Specification
