# Agent Loop

Aliases: Agent Loop, agentic loop

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Agent Loop xuất hiện khi AI agent không chỉ trả lời một lần mà lặp qua các bước quan sát, lập kế hoạch, gọi tool, đọc kết quả và quyết định bước tiếp theo.

## Boundary / Ranh giới

### Nó là gì

Agent Loop là vòng lặp điều phối agent: nhận goal/context, decide next action, call tool hoặc answer, observe result, update state và tiếp tục cho tới khi hoàn thành hoặc dừng.

### Nó không phải là gì

Agent Loop không phải chain prompt tuyến tính đơn giản. Loop có state, stop condition, tool boundary và risk runaway/cost nếu không giới hạn.

## Core Mechanism / Cơ chế lõi

Orchestrator gửi state hiện tại cho model/planner, nhận action proposal, kiểm tra policy/permission, chạy tool nếu được phép, ghi observation vào trace rồi lặp lại cho tới success, failure, timeout hoặc max step.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế agent workflow, debug loop bị kẹt, tool call sai, cost tăng, state drift hoặc approval/policy gate trong agent system.

## Output / Artifact nên có

- Loop state schema
- Step limit/timeout
- Tool/action contract
- Observation/trace log
- Stop condition và failure handling

## Decision Checklist / Câu hỏi kiểm tra

- Agent dừng khi nào?
- Step limit và timeout là bao nhiêu?
- Tool call có policy/approval không?
- Observation nào được đưa lại vào context?
- Trace có đủ để replay/debug không?

## Failure Modes / Cách nó gây lỗi

- Loop không có stop condition rõ nên chạy vòng.
- Tool result được hiểu sai làm action tiếp theo sai.
- State/context phình làm mất thông tin quan trọng.
- Permission quá rộng làm agent gọi tool nguy hiểm.
- Không có trace nên không biết bước nào sai.

## Khi nào chưa cần hoặc dễ over-engineer

- Task đơn giản hỏi-đáp một lượt chưa cần agent loop.
- Không nên thêm loop/tool nếu workflow deterministic code thường xử lý rõ hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Agent]] vì agent loop là cơ chế chạy của agent.
- [[Tool Use]] vì loop thường quyết định và gọi tool.
- [[Timeout]] vì loop cần giới hạn thời gian và bước.
- [[Logging]] vì trace từng step rất quan trọng để debug.
- [[Jailbreak]] vì loop có tool/action nên guardrail cần nghiêm hơn chat thường.

## Liên quan rộng

- Agent orchestration
- Planner executor
- Tool approval

## Keywords / Từ khóa tìm kiếm

- Agent Loop
- agentic loop
- AI agent loop
- tool loop
- agent trace
- max steps
- agent loop debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
