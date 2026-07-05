# System Prompt

Aliases: System Prompt, system instruction

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

System Prompt xuất hiện khi AI app cần đặt vai trò, nguyên tắc, boundary, output format, tool policy hoặc instruction ưu tiên cao cho model trước user message.

## Boundary / Ranh giới

### Nó là gì

System Prompt là instruction cấp hệ thống được đưa vào context để định hướng behavior của model trong một session/request.

### Nó không phải là gì

System Prompt không phải security boundary tuyệt đối. Nó có thể bị prompt injection/jailbreak làm suy yếu nếu runtime không có guardrail, validation và permission enforcement.

## Core Mechanism / Cơ chế lõi

Runtime compose system prompt với developer/app instruction, user input, retrieved context và tool result. Model dùng instruction này để tạo output, nhưng enforcement thật phải nằm ở runtime khi có tool/data/action nhạy cảm.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế chatbot/RAG/agent behavior, output format, safety instruction, prompt versioning hoặc debug vì sao model trả lời lệch role/policy.

## Output / Artifact nên có

- System prompt text
- Version/change history
- Scope and intended behavior
- Eval/regression cases
- Runtime guardrail boundary note

## Decision Checklist / Câu hỏi kiểm tra

- Prompt đang định hướng behavior nào?
- Instruction có rõ priority và boundary không?
- Prompt có quá dài hoặc mâu thuẫn không?
- Có eval trước/sau khi sửa prompt không?
- Policy quan trọng có được enforce ngoài prompt không?

## Failure Modes / Cách nó gây lỗi

- System prompt mơ hồ làm behavior không ổn định.
- Prompt quá nhiều rule xung đột làm model chọn sai.
- Prompt bị coi là security layer duy nhất.
- User/context injection làm model bỏ qua instruction mong muốn.
- Không version prompt nên không trace được regression.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype một task đơn giản có thể dùng prompt ngắn trước.
- Không nên nhồi mọi policy vào system prompt nếu cần runtime enforcement rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Prompt Template]] vì system prompt thường là một template/versioned artifact.
- [[Prompt Versioning]] vì thay đổi system prompt cần trace và rollback.
- [[Prompt Injection]] vì context/user input có thể cố ghi đè instruction.
- [[Guardrail]] vì guardrail bổ sung enforcement ngoài prompt.

## Liên quan rộng

- Instruction hierarchy
- Prompt design
- AI behavior contract

## Keywords / Từ khóa tìm kiếm

- System Prompt
- system instruction
- prompt hierarchy
- AI system prompt
- prompt versioning
- prompt injection
- system prompt debugging

## Source trace

- OpenAI documentation
- Anthropic prompt engineering docs
