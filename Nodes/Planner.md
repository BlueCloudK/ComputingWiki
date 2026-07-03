# Planner

Aliases: AI planner, planning module, bộ lập kế hoạch agent

Type: AI / Agent Engineering

## Context / Ngữ cảnh

Planner là phần của agent hoặc workflow AI chịu trách nhiệm chia mục tiêu thành bước, chọn thứ tự hành động và điều phối tool/model.

## Boundary / Ranh giới

### Nó là gì

Planner quyết định “làm gì tiếp theo” dựa trên goal, state, tool availability, memory và feedback từ bước trước.

### Nó không phải là gì

Nó không phải toàn bộ agent; executor, memory, tool permission, guardrail và evaluation vẫn là phần riêng.

## Core Mechanism / Cơ chế lõi

Planner tạo hoặc cập nhật plan, chọn action tiếp theo, theo dõi trạng thái hoàn thành và điều chỉnh khi tool fail hoặc context thay đổi.

## Project Role / Vai trò trong dự án

Node này giúp thiết kế agent workflow không bị loop, không gọi tool bừa và có thể debug vì sao agent chọn một chuỗi hành động.

## Output / Artifact nên có

- Plan object hoặc checklist action
- Tool selection policy
- Trace log ghi plan change và reason

## Decision Checklist / Câu hỏi kiểm tra

- Planner có biết goal, constraints và done condition không?
- Khi tool fail, planner retry, fallback hay dừng?
- Plan có bị lộ dữ liệu nhạy cảm vào prompt/log không?
- Có giới hạn số bước để tránh loop không?

## Failure Modes / Cách nó gây lỗi

- Agent loop vô hạn vì không có done condition rõ
- Chọn tool sai vì planner không hiểu capability hoặc permission
- Plan quá dài làm context window bị đẩy mất dữ liệu quan trọng

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần planner riêng nếu task chỉ là một prompt hoặc một tool call đơn giản
- Dễ over-engineer nếu thêm multi-step planning trước khi workflow thật sự cần branching

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Agent]] vì planner thường là một thành phần trong agent loop
- [[Tool Calling]] vì plan thường chuyển thành chuỗi tool call có kiểm soát

## Liên quan rộng

- Agent architecture
- Workflow orchestration
- AI reliability

## Keywords / Từ khóa tìm kiếm

- Planner
- AI planner
- planning module
- agent planning
- task decomposition
- action selection
- agent loop
- bộ lập kế hoạch agent

## Source trace

- OpenAI Agents SDK documentation
- ReAct and tool-using agent references
