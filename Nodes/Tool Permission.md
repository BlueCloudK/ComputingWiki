# Tool Permission

Aliases: Tool Permission, tool access policy

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Tool Permission xuất hiện khi AI agent/app có thể gọi tool như file, database, email, calendar, shell, browser, API hoặc cloud action và cần kiểm soát quyền theo task/user/context.

## Boundary / Ranh giới

### Nó là gì

Tool Permission là policy quyết định agent được gọi tool nào, với argument nào, trên resource nào, ở chế độ read/write nào và có cần approval không.

### Nó không phải là gì

Tool Permission không phải chỉ là prompt nhắc model “đừng làm sai”. Quyền tool phải được enforce ở runtime/gateway/orchestrator, không chỉ dựa vào lời model.

## Core Mechanism / Cơ chế lõi

Agent đề xuất tool call. Runtime kiểm tra user/session/task policy, resource scope, risk level và approval state. Tool runner chỉ execute khi policy cho phép, rồi ghi trace/audit log.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế agent gateway, approval flow, least privilege tool access, audit log hoặc debug tool call bị deny/execute sai.

## Output / Artifact nên có

- Tool permission matrix
- Read/write/resource scope
- Approval rule
- Deny/fallback behavior
- Audit log schema

## Decision Checklist / Câu hỏi kiểm tra

- Tool này có read-only hay write action?
- Resource scope nhỏ nhất là gì?
- User/task nào được quyền gọi?
- Action nào cần human approval?
- Tool call có audit trace không?

## Failure Modes / Cách nó gây lỗi

- Agent có quyền tool rộng hơn task cần.
- Permission chỉ nằm trong prompt, runtime không enforce.
- Tool argument không validate nên gọi sai resource.
- Approval bị bypass ở retry/resume path.
- Không có audit log nên không biết action nào đã chạy.

## Khi nào chưa cần hoặc dễ over-engineer

- Chatbot không có tool/action nhạy cảm có thể dùng permission đơn giản.
- Không nên cấp write tool trước khi read-only flow và audit ổn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Agent]] vì agent tool use cần permission boundary.
- [[Tool Use]] vì permission kiểm soát tool call.
- [[Least Privilege]] vì tool nên được cấp quyền tối thiểu.
- [[Jailbreak]] vì jailbreak có impact lớn hơn khi tool permission yếu.

## Liên quan rộng

- Agent gateway
- Human approval
- Tool audit

## Keywords / Từ khóa tìm kiếm

- Tool Permission
- tool access policy
- agent tool permission
- tool allowlist
- tool approval
- tool audit
- tool permission debugging

## Source trace

- OpenAI documentation
- OWASP LLM guidance
