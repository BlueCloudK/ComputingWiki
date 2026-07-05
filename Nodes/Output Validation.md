# Output Validation

Aliases: Output Validation, output schema validation

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Output Validation xuất hiện khi AI output cần đúng schema, đúng format, đúng policy hoặc đủ điều kiện an toàn trước khi đưa cho user hoặc downstream system.

## Boundary / Ranh giới

### Nó là gì

Output Validation là bước kiểm tra output sau generation: schema, field required, type, citation, policy, tool result, business rule hoặc safety constraint.

### Nó không phải là gì

Output Validation không thay thế prompt tốt. Nó là guardrail cuối để phát hiện và xử lý output sai trước khi gây lỗi.

## Core Mechanism / Cơ chế lõi

System parse output, validate bằng schema/rule/judge, trả success hoặc error. Nếu fail, pipeline có thể retry, repair, fallback, block hoặc yêu cầu human review.

## Project Role / Vai trò trong dự án

Dùng node này khi AI output feed vào API, UI, report, database, tool call hoặc automation có risk nếu format/nội dung sai.

## Output / Artifact nên có

- Output schema
- Validation rules
- Failure handling policy
- Retry/repair strategy
- Validation error log

## Decision Checklist / Câu hỏi kiểm tra

- Output cần schema nào?
- Field nào bắt buộc?
- Nếu validation fail thì retry, repair hay block?
- Có validate citation/evidence không?
- Downstream system có chịu được partial output không?

## Failure Modes / Cách nó gây lỗi

- Chỉ tin prompt nên output sai format làm parser crash.
- Validation quá lỏng để lọt field sai.
- Validation quá cứng làm block output hợp lệ.
- Retry không giới hạn gây cost/latency cao.
- Error log thiếu context nên khó debug.

## Khi nào chưa cần hoặc dễ over-engineer

- Chat tự do không downstream automation có thể dùng validation nhẹ.
- Không nên validate bằng rule phức tạp hơn requirement thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Validation]] vì output validation là validation ở boundary AI output.
- [[Prompt Regression]] vì prompt change dễ làm output schema regress.
- [[RAG Evaluation]] vì RAG output cần validate grounding/citation.
- [[AI Agent]] vì agent output có thể kích hoạt action/tool.

## Liên quan rộng

- Structured output
- Guardrails
- Parser safety

## Keywords / Từ khóa tìm kiếm

- Output Validation
- output schema validation
- structured output
- JSON schema validation
- guardrails
- output repair
- output validation debugging

## Source trace

- OpenAI documentation
- OWASP LLM guidance
