# Prompt Regression

Aliases: Prompt Regression, prompt regression test

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Prompt Regression xuất hiện khi thay đổi prompt có thể làm hệ thống AI trả lời kém hơn, sai format, mất policy, sai tool call hoặc giảm grounding.

## Boundary / Ranh giới

### Nó là gì

Prompt Regression là lỗi hành vi xuất hiện sau khi sửa prompt, system message, tool instruction, output schema hoặc prompt template.

### Nó không phải là gì

Prompt Regression không chỉ là model trả lời khác câu chữ. Regression là khi behavior quan trọng tệ hơn so với baseline hoặc vi phạm contract.

## Core Mechanism / Cơ chế lõi

Team lưu prompt version, chạy eval dataset trước/sau thay đổi, so sánh score, format, tool trace, citation và failed cases. Prompt change chỉ nên merge/deploy khi regression quan trọng được xử lý.

## Project Role / Vai trò trong dự án

Dùng node này khi chỉnh prompt RAG/agent, đổi role instruction, thêm guardrail, thay output format hoặc debug vì sao bản mới trả lời tệ hơn bản cũ.

## Output / Artifact nên có

- Prompt version/diff
- Eval report trước/sau
- Failed case list
- Output schema/format check
- Rollback prompt version nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Prompt đổi phần nào và vì sao?
- Baseline prompt là version nào?
- Case critical có tệ hơn không?
- Format/tool/citation contract còn đúng không?
- Có cách rollback nhanh không?

## Failure Modes / Cách nó gây lỗi

- Prompt fix một case nhưng phá case khác.
- Prompt dài hơn làm mất context quan trọng.
- Instruction mới xung đột instruction cũ.
- Output format đổi làm downstream parser lỗi.
- Không version prompt nên khó rollback.

## Khi nào chưa cần hoặc dễ over-engineer

- Prompt thử nghiệm cá nhân có thể ghi version nhẹ trước.
- Không nên build prompt registry phức tạp nếu chưa có eval dataset.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Prompt Registry]] vì registry giúp version và rollback prompt.
- [[Offline Evaluation]] vì prompt regression cần eval trước/sau.
- [[Output Validation]] vì format/schema thường regress sau prompt change.
- [[RAG Evaluation]] vì prompt RAG ảnh hưởng grounding/citation.

## Liên quan rộng

- Prompt versioning
- LLM regression testing
- AI release safety

## Keywords / Từ khóa tìm kiếm

- Prompt Regression
- prompt regression test
- prompt version
- prompt diff
- LLM regression
- prompt eval
- prompt regression debugging

## Source trace

- OpenAI documentation
- Anthropic prompt engineering docs
