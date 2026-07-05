# Jailbreak

Aliases: Jailbreak, LLM Jailbreak

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Jailbreak xuất hiện khi người dùng hoặc input bên ngoài cố làm AI app bỏ qua policy, instruction, role boundary hoặc workflow guardrail đã được thiết kế.

## Boundary / Ranh giới

### Nó là gì

Jailbreak là nhóm kỹ thuật/attempt nhằm khiến model hoặc AI workflow hành xử trái với ràng buộc mong muốn, ví dụ bỏ qua system instruction, tiết lộ thông tin không nên lộ hoặc thực hiện action không phù hợp.

### Nó không phải là gì

Jailbreak không chỉ là prompt injection trong RAG. Prompt injection thường lợi dụng instruction trong dữ liệu/context; jailbreak có thể là trực tiếp từ user hoặc qua nhiều bước tương tác.

## Core Mechanism / Cơ chế lõi

Attack thường tạo xung đột instruction, đổi vai trò, tạo ngoại lệ giả, ép format, chia nhỏ yêu cầu hoặc lợi dụng context dài để làm model ưu tiên sai instruction. Defense cần nhiều lớp: instruction hierarchy, input/output validation, tool permission và eval.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế guardrail cho chatbot/RAG/agent, viết test red-team, phân loại failure mode hoặc review hệ thống có tool/action nhạy cảm.

## Output / Artifact nên có

- Jailbreak test cases
- Policy/guardrail mapping
- Refusal/allow behavior expected
- Output validation rule
- Incident/debug note nếu case lọt qua

## Decision Checklist / Câu hỏi kiểm tra

- App có policy/action nào cần bảo vệ?
- Jailbreak target là output, data access hay tool action?
- Có test negative/edge case không?
- Output có được validate trước khi đi tiếp không?
- Tool permission có tách khỏi lời model không?

## Failure Modes / Cách nó gây lỗi

- Chỉ dựa vào system prompt, không có validation/tool boundary.
- Test jailbreak quá ít và không đại diện use case thật.
- Model từ chối quá rộng làm giảm UX hợp lệ.
- Tool action tin vào output model mà không kiểm tra permission.
- Log thiếu trace nên không biết guardrail fail ở lớp nào.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype không có dữ liệu/action nhạy cảm có thể bắt đầu bằng test nhỏ.
- Không nên dùng guardrail phức tạp nếu chưa xác định asset và policy cần bảo vệ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Prompt Injection]] vì cả hai đều là failure mode instruction/guardrail trong AI app.
- [[AI Evaluation]] vì jailbreak cần test/eval định kỳ.
- [[Output Validation]] vì output cần được kiểm tra trước khi dùng tiếp.
- [[AI Agent]] vì agent có tool/action nên jailbreak có impact lớn hơn chat thường.

## Liên quan rộng

- AI safety testing
- Red teaming
- Guardrails

## Keywords / Từ khóa tìm kiếm

- Jailbreak
- LLM jailbreak
- AI jailbreak
- guardrail bypass
- red team test
- prompt attack
- jailbreak debugging

## Source trace

- OpenAI documentation
- OWASP LLM guidance
