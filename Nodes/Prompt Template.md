# Prompt Template

Aliases: Prompt Template, prompt template

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Prompt Template xuất hiện khi AI app cần tái sử dụng prompt với biến đầu vào như user query, context, tool result, policy hoặc output schema.

## Boundary / Ranh giới

### Nó là gì

Prompt Template là cấu trúc prompt có placeholder/variable và rule render để tạo prompt cuối cùng cho model theo từng request.

### Nó không phải là gì

Prompt Template không phải prompt text tĩnh đơn giản. Nếu biến, escaping, context order hoặc output contract sai, template có thể tạo prompt hỏng ở runtime.

## Core Mechanism / Cơ chế lõi

Template định nghĩa phần cố định và biến. Runtime bind input vào biến, render prompt cuối, gửi tới model và thường gắn version/eval để kiểm soát regression.

## Project Role / Vai trò trong dự án

Dùng node này khi debug prompt render sai, thiếu context, injection qua variable, output format lệch hoặc nhiều flow dùng chung prompt logic.

## Output / Artifact nên có

- Template text
- Variable schema
- Escaping/sanitization rule
- Example rendered prompt
- Version/eval result nếu production

## Decision Checklist / Câu hỏi kiểm tra

- Variable nào bắt buộc và type là gì?
- Input có được escape hoặc boundary rõ không?
- Context order có ổn định không?
- Rendered prompt có được snapshot/test không?
- Template version có trace với output không?

## Failure Modes / Cách nó gây lỗi

- Placeholder thiếu làm prompt render lỗi.
- Variable chứa instruction làm prompt bị nhiễu.
- Context quá dài làm mất phần quan trọng.
- Template update phá output schema.
- Không log rendered prompt/debug sample nên khó trace.

## Khi nào chưa cần hoặc dễ over-engineer

- Prompt thử nghiệm một lần có thể viết trực tiếp trước.
- Không nên tạo template engine phức tạp nếu chỉ có vài prompt đơn giản.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Prompt Versioning]] vì template cần version để rollback/eval.
- [[Prompt Regression]] vì template change có thể làm behavior regress.
- [[Output Validation]] vì template thường quy định schema output.
- [[Jailbreak]] vì variable/context boundary yếu có thể làm prompt bị thao túng.

## Liên quan rộng

- Prompt rendering
- Template variable
- Structured output

## Keywords / Từ khóa tìm kiếm

- Prompt Template
- prompt template
- template variable
- rendered prompt
- prompt rendering
- prompt template debugging

## Source trace

- OpenAI documentation
- Anthropic prompt engineering docs
