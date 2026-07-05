# Tool Error

Aliases: Tool Error, tool call error

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Tool Error xuất hiện khi AI agent hoặc tool runner gọi tool nhưng tool trả lỗi, timeout, permission deny, validation fail hoặc output không parse được.

## Boundary / Ranh giới

### Nó là gì

Tool Error là failure object/signal mô tả tool call không hoàn tất đúng contract, kèm loại lỗi, message, retryability và context cần để agent/runtime xử lý.

### Nó không phải là gì

Tool Error không phải lúc nào cũng là lỗi của model. Nó có thể đến từ schema, permission, network, external API, resource state hoặc tool implementation.

## Core Mechanism / Cơ chế lõi

Tool runner validate input, execute tool, bắt exception/status lỗi, normalize thành error type và trả observation cho agent loop hoặc orchestration layer để retry, fallback, ask user hoặc stop.

## Project Role / Vai trò trong dự án

Dùng node này khi debug agent fail, tool output hỏng, retry loop, permission deny, timeout hoặc khi thiết kế error handling cho tool use production.

## Output / Artifact nên có

- Error type taxonomy
- Tool call input/output trace
- Retryable vs non-retryable rule
- User-facing fallback message
- Audit/debug log

## Decision Checklist / Câu hỏi kiểm tra

- Error thuộc schema, permission, timeout, network hay business state?
- Có nên retry không?
- Agent có được thấy toàn bộ error message không?
- Error có chứa secret/sensitive data không?
- Fallback hoặc escalation là gì?

## Failure Modes / Cách nó gây lỗi

- Trả raw exception chứa secret cho model/user.
- Không phân loại lỗi nên retry sai.
- Tool fail nhưng agent tiếp tục như thành công.
- Error message quá mơ hồ làm agent sửa sai hướng.
- Không có trace nên không biết tool nào lỗi với argument nào.

## Khi nào chưa cần hoặc dễ over-engineer

- Tool prototype đơn giản có thể bắt đầu bằng error object tối thiểu.
- Không nên expose lỗi nội bộ đầy đủ nếu tool chạm dữ liệu nhạy cảm.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Tool Use]] vì tool error là failure mode trực tiếp của tool call.
- [[Tool Retry]] vì retry policy cần phân loại tool error.
- [[Tool Schema]] vì schema lỗi là một loại tool error phổ biến.
- [[Logging]] vì trace tool error cần cho debug/audit.

## Liên quan rộng

- Error handling
- Agent observation
- Tool runner

## Keywords / Từ khóa tìm kiếm

- Tool Error
- tool call error
- agent tool error
- tool timeout
- tool permission denied
- tool validation error
- tool error debugging

## Source trace

- OpenAI documentation
- Google SRE Books
