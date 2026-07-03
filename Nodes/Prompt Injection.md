# Prompt Injection

Aliases: prompt injection attack, tấn công prompt

Type: AI Security

## Context / Ngữ cảnh

Prompt Injection xuất hiện khi LLM app nhận instruction hoặc nội dung không tin cậy từ user, webpage, tài liệu, email, RAG result hoặc tool output. Nó đặc biệt nguy hiểm khi model có quyền gọi tool, đọc dữ liệu riêng, ghi dữ liệu, gửi request hoặc quyết định workflow.

## Boundary / Ranh giới

### Nó là gì

Prompt Injection là kiểu tấn công trong đó dữ liệu không tin cậy được viết như instruction để làm model bỏ qua policy, lộ dữ liệu, dùng tool sai hoặc làm theo mục tiêu của attacker. Trọng tâm không chỉ là “prompt xấu”, mà là boundary giữa trusted instruction và untrusted content bị trộn lẫn.

### Nó không phải là gì

Prompt Injection không phải mọi câu prompt sai hoặc hallucination. Hallucination là model trả lời sai; prompt injection là input cố tình thao túng instruction/control flow. Nó cũng không thể xử lý chỉ bằng “system prompt mạnh hơn” nếu app vẫn đưa dữ liệu/tool không tin cậy vào cùng context mà không có guardrail.

## Core Mechanism / Cơ chế lõi

LLM đọc context như chuỗi token và có thể bị nội dung không tin cậy mô phỏng instruction. Nếu app không tách quyền, không kiểm soát tool, không lọc output và không kiểm tra hành động trước khi thực thi, model có thể ưu tiên instruction độc hại hoặc dùng tool theo cách vượt ý định ban đầu.

## Project Role / Vai trò trong dự án

Prompt Injection ảnh hưởng trực tiếp tới thiết kế AI chatbot, RAG app, agent, workflow automation và AI security testing. Khi build AI app, team phải xác định nguồn nào là trusted/untrusted, tool nào nguy hiểm, dữ liệu nào không được lộ, và hành động nào cần policy/approval trước khi thực thi.

## Output / Artifact nên có

- Threat model cho prompt/context boundary
- Danh sách nguồn untrusted: user input, web page, document, retrieved chunk, tool output
- Tool permission matrix: tool nào read-only, tool nào write/destructive, tool nào cần approval
- Prompt injection test cases cho RAG, agent và tool-calling flow
- Policy/guardrail rule cho dữ liệu nhạy cảm, tool use, external request và output filtering

## Decision Checklist / Câu hỏi kiểm tra

- Nội dung nào trong context là trusted instruction, nội dung nào là untrusted data?
- Retrieved document hoặc webpage có thể chứa instruction độc hại không?
- Model có quyền gọi tool nào có side effect như gửi email, ghi DB, gọi API hoặc xóa file không?
- Tool call có được validate bằng policy ngoài model không?
- Có approval step cho action nguy hiểm không?
- Có test case kiểu “ignore previous instructions”, data exfiltration và malicious retrieved chunk không?
- Output có thể leak system prompt, secret, private document hoặc tool result nhạy cảm không?

## Failure Modes / Cách nó gây lỗi

- RAG document chứa instruction độc hại khiến model bỏ qua câu hỏi thật hoặc lộ dữ liệu.
- Agent bị lừa gọi tool ngoài ý định, ví dụ gửi email, tạo ticket, gọi API hoặc thay đổi config.
- Model tóm tắt email/webpage và làm theo instruction bên trong nội dung đó.
- App tin model tự quyết định quyền truy cập, dẫn tới data exfiltration.
- Guardrail chỉ nằm trong prompt nên bị instruction injection vượt qua.
- Log/debug output vô tình ghi lại secret hoặc nội dung nhạy cảm do prompt injection kích hoạt.

## Khi nào chưa cần hoặc dễ over-engineer

- Chatbot nội bộ không dùng RAG, không có tool, không truy cập dữ liệu riêng có thể bắt đầu bằng test case đơn giản.
- Không nên mua/thêm nhiều guardrail layer nếu chưa xác định rõ asset, tool permission và attack path.
- App chỉ dùng LLM để rewrite text không nhạy cảm có risk thấp hơn agent có tool và private data.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[RAG]] vì retrieved content có thể chứa instruction độc hại và đi vào prompt.
- [[AI Agent]] vì agent có tool/action nên prompt injection có thể biến thành hành động thật.
- [[AI Gateway]] vì gateway có thể enforce policy, logging, routing và guardrail quanh model/tool call.
- [[RAG Leakage]] vì prompt injection thường được dùng để ép model lộ tài liệu hoặc context riêng.

## Liên quan rộng

- LLM application security
- Tool permission
- Data exfiltration
- Human approval workflow
- Security testing

## Keywords / Từ khóa tìm kiếm

- Prompt Injection
- prompt injection attack
- tấn công prompt
- indirect prompt injection
- malicious instruction
- untrusted content
- RAG prompt injection
- tool calling attack
- data exfiltration
- ignore previous instructions
- system prompt leakage
- AI security testing
- prompt boundary
- injection qua tài liệu

## Source trace

- OWASP Top 10 for LLM Applications
- OWASP LLM Prompt Injection Prevention Cheat Sheet
