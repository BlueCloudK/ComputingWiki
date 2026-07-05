# Policy Check

Aliases: Policy Check, policy evaluation

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Policy Check xuất hiện khi AI workflow, tool call, deploy step hoặc user request cần được kiểm tra với rule an toàn, quyền hạn, compliance hoặc business policy trước khi tiếp tục.

## Boundary / Ranh giới

### Nó là gì

Policy Check là bước evaluate một input/action/context với policy đã định nghĩa để trả về allow, deny, require approval, redact hoặc fallback.

### Nó không phải là gì

Policy Check không phải lời nhắc model tự cư xử tốt. Nó nên được enforce ở runtime/pipeline/gateway bằng rule và audit rõ.

## Core Mechanism / Cơ chế lõi

System thu context như user, role, action, resource, tool, environment và risk level. Policy engine hoặc rule check quyết định action tiếp theo; kết quả được log để audit/debug.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế guardrail, tool permission, deployment gate, approval flow, access control hoặc debug vì sao request/action bị deny.

## Output / Artifact nên có

- Policy rule set
- Input context schema
- Decision result: allow/deny/approval
- Reason code
- Audit log

## Decision Checklist / Câu hỏi kiểm tra

- Policy đang bảo vệ asset/risk nào?
- Input context có đủ để quyết định không?
- Deny reason có rõ để debug không?
- Có approval path cho case biên không?
- Policy có thể bị bypass qua route/tool khác không?

## Failure Modes / Cách nó gây lỗi

- Policy chỉ nằm trong prompt, runtime không enforce.
- Rule thiếu context nên allow/deny sai.
- Deny không có reason làm người dùng/operator không biết sửa gì.
- Route phụ bypass policy check chính.
- Policy quá chặt làm workflow hợp lệ bị block liên tục.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype nội bộ không có action nhạy cảm có thể dùng checklist nhẹ.
- Không nên xây policy engine phức tạp nếu chỉ có vài rule rõ ràng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Guardrail]] vì policy check là một dạng guardrail runtime.
- [[Tool Permission]] vì tool access cần policy decision.
- [[Deployment Gate]] vì deploy gate có thể chạy policy check.
- [[Least Privilege]] vì policy thường encode quyền tối thiểu.

## Liên quan rộng

- Policy engine
- Approval flow
- Access decision

## Keywords / Từ khóa tìm kiếm

- Policy Check
- policy evaluation
- policy engine
- allow deny
- approval required
- runtime policy
- policy check debugging

## Source trace

- OWASP LLM guidance
- Open Policy Agent documentation
