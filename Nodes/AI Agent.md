# AI Agent

Aliases: AI Agent, ai agent, Agent

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

AI Agent xuất hiện khi LLM system không chỉ trả lời một lượt mà còn lập kế hoạch, chọn tool, gọi API, đọc/ghi state, quan sát kết quả và tiếp tục hành động để hoàn thành task. Nó thường dùng trong coding assistant, research assistant, workflow automation, support automation hoặc internal operations bot.

## Boundary / Ranh giới

### Nó là gì

AI Agent là hệ thống dùng model làm reasoning/control layer để quyết định bước tiếp theo trong một workflow. Một agent thường có instruction, task state, tool access, memory/context, planner hoặc policy, execution loop và cơ chế quan sát kết quả sau mỗi action.

### Nó không phải là gì

AI Agent không phải mọi chatbot dùng LLM. Nếu hệ thống chỉ nhận prompt và trả lời một lần, chưa có tool/state/action loop thì chưa cần gọi là agent. Agent cũng không nên được tin hoàn toàn tự do; tool permission, approval, logging và guardrail phải nằm ngoài model khi hành động có rủi ro.

## Core Mechanism / Cơ chế lõi

Agent loop thường gồm: nhận goal, phân rã task, chọn action/tool, thực thi, quan sát kết quả, cập nhật state/memory, rồi lặp lại cho tới khi hoàn thành hoặc dừng. Rủi ro tăng khi agent có tool side effect như gửi email, sửa DB, deploy, xóa file hoặc gọi external API.

## Project Role / Vai trò trong dự án

AI Agent ảnh hưởng tới architecture, security, observability, evaluation và cost của AI app. Khi build agent, team phải quyết định tool nào được phép, action nào cần approval, state được lưu ở đâu, loop dừng thế nào, ai chịu trách nhiệm khi agent sai và cách replay/debug một run.

## Output / Artifact nên có

- Agent capability map: goal, tool, permission, input/output, side effect
- Execution loop design: planner, tool runner, observer, memory/state, stopping condition
- Tool permission matrix và approval policy cho action nguy hiểm
- Trace format cho mỗi run: prompt, tool call, result, decision, error
- Eval/test set cho task success, tool misuse, prompt injection và unsafe action

## Decision Checklist / Câu hỏi kiểm tra

- Agent thực sự cần tự hành động nhiều bước hay chỉ cần chatbot/workflow cố định?
- Tool nào read-only, tool nào write/destructive, tool nào cần approval?
- Agent có stopping condition, timeout và max step không?
- State/memory của agent được lưu ở đâu và có thể replay/debug không?
- Policy kiểm tra tool call nằm ngoài model hay chỉ nằm trong prompt?
- Có test prompt injection/tool misuse trước khi cho agent dùng dữ liệu/tool thật không?
- Khi agent fail giữa chừng, rollback hoặc human handoff thế nào?

## Failure Modes / Cách nó gây lỗi

- Agent loop không dừng, gọi tool lặp lại và tốn cost/tài nguyên.
- Tool permission quá rộng làm agent có thể đọc/ghi/xóa ngoài phạm vi task.
- Prompt injection khiến agent dùng tool theo instruction độc hại từ webpage/document/user.
- Không có trace làm khó biết agent đã quyết định sai ở bước nào.
- Memory/state sai khiến agent tiếp tục theo kế hoạch cũ dù context đã đổi.
- Agent tự tin hoàn thành task nhưng artifact/output không được verify bằng test hoặc reviewer.

## Khi nào chưa cần hoặc dễ over-engineer

- Task tuyến tính có rule rõ có thể dùng workflow bình thường thay vì agent tự quyết.
- Không nên thêm multi-agent nếu một agent hoặc pipeline cố định đã đủ kiểm soát.
- Không nên cấp tool write/deploy/delete trước khi có approval, sandbox và audit log.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Tool Calling]] vì agent thường hành động thông qua tool call.
- [[Agent Memory]] vì agent cần state/memory để duy trì context qua nhiều bước.
- [[Prompt Injection]] vì agent có tool nên prompt injection có thể biến thành hành động thật.
- [[AI Gateway]] vì gateway có thể kiểm soát routing, policy và audit quanh agent/tool call.
- [[AI Evaluation]] vì agent cần eval theo task success và safety, không chỉ chất lượng câu trả lời.

## Liên quan rộng

- Workflow automation
- Human-in-the-loop approval
- Observability
- Security testing
- Cost control

## Keywords / Từ khóa tìm kiếm

- AI Agent
- ai agent
- Agent
- agent loop
- tool using agent
- tool calling agent
- planner executor
- agent workflow
- autonomous agent
- human in the loop
- agent trace
- agent permission
- agent evaluation
- agent safety
- multi-step AI system

## Source trace

- OpenAI documentation
- Anthropic tool use documentation
- LangChain agents documentation
