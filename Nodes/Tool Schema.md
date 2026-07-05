# Tool Schema

Aliases: Tool Schema, tool input schema

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Tool Schema xuất hiện khi AI agent hoặc function calling system cần mô tả tool bằng name, description, input parameters, output shape và constraint để model/runtime gọi đúng.

## Boundary / Ranh giới

### Nó là gì

Tool Schema là contract máy-đọc được cho tool call: tool làm gì, nhận argument nào, type/required field ra sao và output trả về dạng gì.

### Nó không phải là gì

Tool Schema không phải permission layer. Schema giúp gọi đúng format; permission/policy vẫn phải kiểm tra tool có được phép chạy hay không.

## Core Mechanism / Cơ chế lõi

Runtime đưa schema cho model hoặc planner. Model tạo tool call theo schema; runtime validate argument, execute tool và trả observation về agent loop. Schema càng rõ, tool call càng ít sai định dạng.

## Project Role / Vai trò trong dự án

Dùng node này khi debug tool call sai field, argument thiếu, output parse fail, agent gọi nhầm tool hoặc cần version hóa contract tool.

## Output / Artifact nên có

- Tool name/description
- Input JSON schema
- Output schema/example
- Validation error behavior
- Version/change note

## Decision Checklist / Câu hỏi kiểm tra

- Field nào bắt buộc?
- Description có đủ rõ để model chọn đúng tool không?
- Argument có enum/range/format rõ không?
- Output có ổn định để bước sau parse không?
- Schema change có backward compatible không?

## Failure Modes / Cách nó gây lỗi

- Description mơ hồ làm model gọi nhầm tool.
- Schema quá lỏng làm argument sai vẫn qua.
- Schema quá phức tạp làm model điền thiếu field.
- Output không có schema nên bước sau parse lỗi.
- Schema đổi nhưng prompt/eval/tool runner chưa cập nhật.

## Khi nào chưa cần hoặc dễ over-engineer

- Tool nội bộ đơn giản có thể bắt đầu bằng schema tối thiểu.
- Không nên nhồi business policy vào schema nếu runtime permission mới là nơi enforce đúng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Tool Use]] vì schema định nghĩa cách gọi tool.
- [[Function Calling]] vì function calling dựa trên schema argument.
- [[Output Validation]] vì tool input/output cần validate.
- [[Tool Permission]] vì schema và permission là hai lớp khác nhau.

## Liên quan rộng

- JSON schema
- Tool contract
- Agent runtime

## Keywords / Từ khóa tìm kiếm

- Tool Schema
- tool input schema
- function calling schema
- JSON schema tool
- tool argument validation
- tool schema debugging

## Source trace

- OpenAI documentation
- JSON Schema documentation
