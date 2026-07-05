# Error Value

Aliases: Error Value, error-as-value

Type: Programming Languages Deep

## Context / Ngữ cảnh

Error Value xuất hiện khi ngôn ngữ hoặc API biểu diễn lỗi như một value được return thay vì ném exception qua control flow ẩn.

## Boundary / Ranh giới

### Nó là gì

Error Value là cách xử lý lỗi bằng return value như `Result`, `Either`, error object, tuple `(value, error)` hoặc status object để caller kiểm tra tường minh.

### Nó không phải là gì

Error Value không tự đảm bảo lỗi được xử lý. Nếu caller bỏ qua error value hoặc unwrap bừa, lỗi vẫn lọt qua và có thể crash hoặc sai dữ liệu.

## Core Mechanism / Cơ chế lõi

Function trả về success value hoặc error value theo contract. Caller phải pattern match/check error, chuyển đổi, wrap context hoặc propagate lên tầng trên.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế API contract, debug lỗi bị bỏ qua, so sánh exception vs result type, hoặc viết code cần error path rõ và testable.

## Output / Artifact nên có

- Return type/error schema
- Caller handling rule
- Propagation/wrapping convention
- Test cho success và failure path
- Logging/context rule nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Caller có bắt buộc kiểm tra error không?
- Error value có đủ context không?
- Error nên recover, retry hay propagate?
- Có phân biệt expected error và bug không?
- API có làm success/error shape rõ không?

## Failure Modes / Cách nó gây lỗi

- Caller ignore error value.
- Error context bị mất khi propagate.
- Success và error shape mơ hồ.
- Dùng error value cho bug unrecoverable làm code rối.
- Không test failure path.

## Khi nào chưa cần hoặc dễ over-engineer

- Script nhỏ có thể dùng exception đơn giản hơn.
- Không nên bọc mọi thứ vào result type nếu framework/language đã có error boundary phù hợp.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Validation]] vì validation thường trả error value có thể xử lý được.
- [[API Contract]] vì API cần định nghĩa error shape rõ.
- [[Runtime]] vì exception/error value là hai mô hình control flow khác nhau.
- [[Unit Test]] vì success/failure path cần được test riêng.

## Liên quan rộng

- Result type
- Exception handling
- Error propagation

## Keywords / Từ khóa tìm kiếm

- Error Value
- error-as-value
- Result type
- Either
- error object
- error propagation
- error value debugging

## Source trace

- Types and Programming Languages
- Rust documentation
- Go documentation
