# Guardrail

Aliases: Guardrail, AI guardrail

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Guardrail xuất hiện khi AI app cần kiểm soát input, output, tool use, policy, safety hoặc data boundary để giảm hành vi sai ngoài ý muốn.

## Boundary / Ranh giới

### Nó là gì

Guardrail là lớp kiểm soát giúp phát hiện, chặn, sửa, yêu cầu approval hoặc log hành vi rủi ro trong AI workflow.

### Nó không phải là gì

Guardrail không phải chỉ là system prompt. Guardrail tốt thường gồm runtime policy, validation, permission, eval, logging và fallback behavior.

## Core Mechanism / Cơ chế lõi

Input/output/tool call đi qua các check như schema validation, policy check, allowlist, classifier, citation check hoặc human approval. Nếu fail, workflow deny, rewrite, ask clarification, fallback hoặc escalate.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế AI app production, RAG leakage prevention, agent tool safety, jailbreak defense, output schema enforcement hoặc audit behavior.

## Output / Artifact nên có

- Guardrail policy matrix
- Input/output validation rules
- Tool permission/approval rule
- Failure/fallback behavior
- Eval and audit log

## Decision Checklist / Câu hỏi kiểm tra

- Guardrail bảo vệ asset/risk nào?
- Check chạy ở input, retrieval, model output hay tool runtime?
- Fail thì deny, ask, rewrite hay escalate?
- Guardrail có metric false positive/false negative không?
- Có bypass path nào không?

## Failure Modes / Cách nó gây lỗi

- Chỉ dựa vào prompt nên bị jailbreak/prompt injection vượt qua.
- Guardrail quá chặt làm block yêu cầu hợp lệ.
- Guardrail quá lỏng làm action/data leak lọt qua.
- Không log reason nên khó debug false positive.
- Tool permission không enforce ở runtime.

## Khi nào chưa cần hoặc dễ over-engineer

- Demo không có dữ liệu/action nhạy cảm có thể bắt đầu bằng validation đơn giản.
- Không nên thêm nhiều guardrail nếu chưa xác định risk và asset cụ thể.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Jailbreak]] vì guardrail cần chống bypass instruction/policy.
- [[Prompt Injection]] vì input/context có thể cố thao túng workflow.
- [[Output Validation]] vì output là điểm guardrail quan trọng.
- [[Tool Permission]] vì agent tool action phải được kiểm soát bằng permission runtime.
- [[Policy Check]] vì policy check là một dạng guardrail rõ ràng.

## Liên quan rộng

- AI safety
- Runtime policy
- Human approval
- Audit logging

## Keywords / Từ khóa tìm kiếm

- Guardrail
- AI guardrail
- input guardrail
- output guardrail
- policy check
- tool guardrail
- guardrail debugging

## Source trace

- OpenAI documentation
- OWASP LLM guidance
