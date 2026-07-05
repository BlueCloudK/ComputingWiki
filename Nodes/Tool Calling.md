# Tool Calling

Aliases: Tool Calling, function calling

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Tool Calling xuất hiện khi model không chỉ trả text mà còn chọn và gọi tool/function/API để lấy dữ liệu, thực hiện hành động hoặc quan sát môi trường.

## Boundary / Ranh giới

### Nó là gì

Tool Calling là cơ chế model/planner tạo structured tool call theo schema, runtime execute tool và đưa observation quay lại model hoặc workflow.

### Nó không phải là gì

Tool Calling không tự đồng nghĩa với agent an toàn. Tool call cần schema, permission, sandbox, timeout, retry, logging và approval nếu có side effect.

## Core Mechanism / Cơ chế lõi

Runtime cung cấp tool schema cho model. Model chọn tool và arguments. Runtime validate, kiểm tra permission, execute tool, nhận result/error rồi đưa observation vào bước tiếp theo của agent loop.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế AI agent, RAG tool retrieval, function calling API, tool runner, audit trace hoặc debug vì sao model gọi nhầm tool/argument.

## Output / Artifact nên có

- Tool list and schema
- Tool permission matrix
- Tool call trace
- Error/retry policy
- Output observation contract

## Decision Checklist / Câu hỏi kiểm tra

- Model có cần tool thật không hay text answer đủ?
- Tool schema có rõ name/description/argument không?
- Tool nào read-only, tool nào có side effect?
- Permission/sandbox được enforce ở đâu?
- Tool result có được validate trước khi dùng tiếp không?

## Failure Modes / Cách nó gây lỗi

- Model gọi nhầm tool vì description mơ hồ.
- Argument sai schema hoặc thiếu field.
- Tool side effect chạy khi chưa approval.
- Tool result bị tin tuyệt đối dù lỗi/stale.
- Không có trace nên không debug được agent làm gì.

## Khi nào chưa cần hoặc dễ over-engineer

- Q&A đơn giản có thể trả lời trực tiếp, chưa cần tool calling.
- Không nên thêm write tool nếu read-only tool và guardrail chưa ổn.

## Gồm những gì

- [[Tool Schema]]
- [[Tool Permission]]
- [[Tool Error]]
- [[Tool Retry]]
- [[Tool Sandbox]]

## Nối mạnh

- [[Tool Use]] vì tool calling là cơ chế cụ thể để agent dùng tool.
- [[Tool Schema]] vì schema định nghĩa format tool call.
- [[Tool Permission]] vì runtime cần quyết định tool nào được gọi.
- [[AI Agent]] vì agent thường lặp giữa reasoning và tool calling.

## Liên quan rộng

- Function calling
- Agent runtime
- Structured action

## Keywords / Từ khóa tìm kiếm

- Tool Calling
- function calling
- agent tool call
- tool schema
- tool observation
- structured tool call
- tool calling debugging

## Source trace

- OpenAI documentation
- Anthropic tool use documentation
