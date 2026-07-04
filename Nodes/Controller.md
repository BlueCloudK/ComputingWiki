# Controller

Aliases: request controller, web controller, controller backend

Type: Backend Engineering

## Context / Ngữ cảnh

Controller xuất hiện khi request ở boundary web/API cần được map tới application logic phù hợp. Nó thường nằm sau router/middleware và trước service/use case layer trong MVC, layered architecture hoặc backend API framework.

## Boundary / Ranh giới

### Nó là gì

Controller là lớp nhận request đã match route, parse input, gọi validation/auth handoff nếu cần, chuyển dữ liệu sang service/use case, rồi map kết quả hoặc lỗi thành response. Nó là adapter giữa giao thức HTTP/API và application logic.

### Nó không phải là gì

Controller không nên chứa business logic chính, query phức tạp hoặc transaction workflow dài. Nó cũng không phải service layer. Nếu controller biết quá nhiều domain rule, database detail hoặc external integration, code dễ khó test và endpoint behavior khó reuse.

## Core Mechanism / Cơ chế lõi

Request đi qua routing/middleware tới controller action. Controller đọc path/query/body/header, gọi validator/mapper, gọi service/use case, bắt lỗi domain/application và trả status code/response DTO phù hợp. Controller tốt mỏng, rõ input/output và đẩy rule nghiệp vụ xuống layer phù hợp.

## Project Role / Vai trò trong dự án

Controller giúp team xác định nơi endpoint bắt đầu trong code, nơi request được chuyển thành command/query, và nơi response/error được chuẩn hóa. Khi debug API, controller là điểm kiểm tra request có vào đúng route không, validation có chạy không, service có được gọi không và lỗi được map ra response thế nào.

## Output / Artifact nên có

- Controller/action map theo endpoint: method/path → controller method → service/use case
- Request DTO/response DTO và validation rule tương ứng
- Error mapping rule: domain error → HTTP status/error body
- Test case cho controller: success, validation fail, unauthorized/forbidden, not found, service error
- Logging/trace convention ở boundary request

## Decision Checklist / Câu hỏi kiểm tra

- Controller có chỉ làm orchestration mỏng hay đang chứa business logic?
- Input validation nằm ở DTO/validator/middleware hay rải trong controller?
- Controller gọi service/use case rõ ràng hay gọi repository/database trực tiếp?
- Error được map thống nhất sang status code và error body không?
- Response DTO có che field nhạy cảm và giữ contract ổn định không?
- Có controller test cho failure path quan trọng không?
- Endpoint metric/log có gắn được tới controller/action không?

## Failure Modes / Cách nó gây lỗi

- Controller phình to chứa business rule làm logic khó test và trùng lặp giữa endpoint.
- Controller gọi database trực tiếp làm transaction/service boundary mơ hồ.
- Error mapping không thống nhất làm client nhận status code/body khó dự đoán.
- Thiếu validation ở boundary làm dữ liệu sai đi sâu vào service/database.
- Response trả entity trực tiếp làm lộ field nội bộ hoặc phá API contract khi entity đổi.
- Controller catch exception quá rộng làm che lỗi thật và trả 200/500 sai.

## Khi nào chưa cần hoặc dễ over-engineer

- App nhỏ có vài endpoint có thể dùng controller đơn giản, chưa cần tách quá nhiều adapter/mapper.
- Không nên tạo controller-service-usecase-command nhiều lớp nếu behavior chưa đủ phức tạp.
- Không nên biến controller thành nơi gom mọi logic chỉ vì “dễ code nhanh”.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Endpoint]] vì controller thường implement endpoint handler.
- [[Service Layer]] vì controller nên gọi service/use case thay vì chứa business logic.
- [[DTO]] vì controller thường nhận/trả request/response DTO.
- [[Validation]] vì controller boundary là nơi quan trọng để validate input.

## Liên quan rộng

- MVC
- Backend architecture
- Request handling
- API error handling

## Keywords / Từ khóa tìm kiếm

- Controller
- request controller
- web controller
- controller backend
- controller action
- endpoint handler
- MVC controller
- thin controller
- request parsing
- response mapping
- error mapping
- controller validation
- controller service layer
- API controller

## Source trace

- Martin Fowler Patterns of Enterprise Application Architecture
- Spring MVC documentation
