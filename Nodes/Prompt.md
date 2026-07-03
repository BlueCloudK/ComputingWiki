# Prompt

Aliases: LLM prompt, model prompt, lời nhắc AI

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Prompt là input hướng dẫn model tạo output, thường gồm task, context, constraint, examples và format mong muốn.

## Boundary / Ranh giới

### Nó là gì

Prompt là lớp giao tiếp giữa application và model, nơi app nói model cần làm gì với dữ liệu và công cụ hiện có.

### Nó không phải là gì

Nó không phải security boundary chắc chắn, không thay thế validation, policy enforcement hoặc eval.

## Core Mechanism / Cơ chế lõi

Model nhận prompt cùng conversation/context window, rồi sinh output theo xác suất dựa trên instruction, retrieved context và lịch sử tương tác.

## Project Role / Vai trò trong dự án

Prompt giúp team debug AI behavior, chuẩn hóa output contract, kiểm soát style và giảm drift giữa các task lặp lại.

## Output / Artifact nên có

- Prompt template có biến đầu vào rõ
- Output contract hoặc schema mong muốn
- Eval set để kiểm tra prompt sau khi đổi

## Decision Checklist / Câu hỏi kiểm tra

- Prompt có tách instruction, context và user input rõ không?
- Output có schema/checker hay chỉ mô tả bằng prose?
- Có test case cho input khó, thiếu dữ liệu hoặc prompt injection không?
- Prompt có chứa secret hoặc dữ liệu không cần thiết không?

## Failure Modes / Cách nó gây lỗi

- Prompt mơ hồ làm output drift theo từng lần chạy
- Trộn user input với instruction làm tăng rủi ro prompt injection
- Không có eval nên sửa prompt làm hỏng case cũ mà không biết

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần prompt framework phức tạp cho tác vụ thử nghiệm nhỏ
- Dễ over-engineer nếu tối ưu wording trước khi có eval và failure case thật

## Gồm những gì

- [[System Prompt]]
- [[User Prompt]]
- [[Developer Prompt]]
- [[Prompt Template]]

## Nối mạnh

- [[Prompt Engineering]] vì prompt là đối tượng chính được thiết kế và kiểm thử
- [[Prompt Injection]] vì prompt boundary dễ bị user input phá nếu không kiểm soát

## Liên quan rộng

- LLM application design
- Output validation
- AI evaluation

## Keywords / Từ khóa tìm kiếm

- Prompt
- LLM prompt
- model prompt
- prompt template
- system prompt
- user prompt
- instruction
- lời nhắc AI
- thiết kế prompt

## Source trace

- OpenAI documentation / prompt engineering
- Anthropic prompt engineering documentation
