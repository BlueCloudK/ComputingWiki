# Data Transfer Object

Aliases: DTO, đối tượng truyền dữ liệu

Type: Code Design / Pattern

## Context / Ngữ cảnh

Data Transfer Object xuất hiện khi dữ liệu đi qua boundary như API request/response, service layer, message queue hoặc external integration. Nó giúp tách shape dữ liệu giao tiếp khỏi entity/domain model/persistence model bên trong.

## Boundary / Ranh giới

### Nó là gì

DTO là object/schema dùng để truyền dữ liệu giữa layer/process/service. DTO thường chỉ chứa data field cần thiết cho một use case hoặc API contract, ví dụ `CreateUserRequest`, `UserResponse`, `OrderSummaryDto`. Nó giúp kiểm soát field nào được nhận/trả và tránh lộ model nội bộ.

### Nó không phải là gì

DTO không phải domain entity và không nên chứa business behavior phức tạp. DTO cũng không phải license để tạo object mapping vô hạn. Nếu DTO chỉ copy y hệt entity ở mọi nơi mà không bảo vệ boundary nào, nó có thể chỉ làm code dài hơn.

## Core Mechanism / Cơ chế lõi

Controller/API nhận request DTO, validation chạy theo schema/rule, service xử lý use case, rồi mapper chuyển entity/domain result sang response DTO. Khi API contract đổi, DTO giúp thay đổi boundary giao tiếp mà không nhất thiết đổi entity/database model.

## Project Role / Vai trò trong dự án

DTO là node cần mở khi thiết kế API contract, tránh over-posting/mass assignment, che field nội bộ, versioning response hoặc giảm coupling giữa frontend/backend. Nó giúp team biết dữ liệu nào public, field nào internal và mapping nằm ở đâu.

## Output / Artifact nên có

- Request DTO và response DTO cho endpoint/use case quan trọng
- Validation rule cho request DTO: required, nullable, enum, range, format
- Mapping rule giữa DTO và domain/entity/model
- API contract/OpenAPI schema nếu endpoint public hoặc nhiều consumer
- Test case cho field thiếu, field thừa, invalid type và sensitive field exposure

## Decision Checklist / Câu hỏi kiểm tra

- DTO này nằm ở boundary nào: API, service, queue hay external integration?
- Có field nào của entity không nên lộ ra response không?
- Request DTO có chống over-posting/mass assignment không?
- DTO có đang leak persistence/domain detail ra consumer không?
- Mapping có rõ ràng và test được không?
- Field optional/nullable/default có khớp API contract không?
- Có cần DTO version mới để tránh breaking change không?

## Failure Modes / Cách nó gây lỗi

- Trả entity trực tiếp làm lộ password hash, internal status hoặc field nhạy cảm.
- Request bind thẳng vào entity làm user set được field không nên set.
- DTO drift khỏi API contract khiến frontend/backend mismatch.
- Mapping thủ công thiếu field làm response mất dữ liệu hoặc update sai.
- DTO quá generic làm validation và ownership field mơ hồ.
- Tạo quá nhiều DTO/mapping layer mà không có boundary thật, làm code khó đọc.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype rất nhỏ một endpoint có thể dùng schema đơn giản trước.
- Không nên tạo DTO riêng cho mọi method nếu shape dữ liệu giống nhau và không có boundary/risk rõ.
- Không nên dùng DTO để che việc API contract chưa được thiết kế rõ.

## Gồm những gì

- [[Encoding and Evolution]]

## Nối mạnh

- [[API Contract]] vì DTO thường hiện thực request/response contract.
- [[Validation]] vì request DTO cần validation rule rõ.
- [[Service Layer]] vì controller thường map DTO rồi gọi service layer.
- [[OpenAPI]] vì DTO/schema có thể sinh hoặc khớp OpenAPI spec.
- [[API Versioning]] vì DTO change có thể tạo breaking change cho consumer.

## Liên quan rộng

- Codebase
- Refactoring
- Frontend backend handoff
- Data modeling

## Keywords / Từ khóa tìm kiếm

- Data Transfer Object
- DTO
- đối tượng truyền dữ liệu
- request DTO
- response DTO
- DTO mapping
- API DTO
- over posting
- mass assignment
- entity exposure
- nullable field
- DTO validation
- API contract DTO
- DTO debugging

## Source trace

- Patterns of Enterprise Application Architecture
- Data Intensive Applications Map / Ch04
