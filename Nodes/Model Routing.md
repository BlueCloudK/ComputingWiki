# Model Routing

Aliases: Model Routing, model routing

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Model Routing xuất hiện trong ai rag and agent engineering là vùng kiến thức về llm app, retrieval, tool use, agent workflow, evaluation, guardrails và production reliability.

## Boundary / Ranh giới

### Nó là gì

Model Routing là khái niệm giúp đặt tên đúng một phần của hệ thống, workflow hoặc failure mode trong vùng AI / RAG / Agent Engineering.

### Nó không phải là gì

Nó không phải keyword để nhồi vào graph; node này chỉ hữu ích khi nối được với artifact, decision hoặc debug path cụ thể.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là hiểu Model Routing nằm ở boundary nào, input/output là gì, state hoặc config nào liên quan, và lỗi thường lộ ra bằng signal nào.

## Project Role / Vai trò trong dự án

Model Routing giúp team thiết kế, review, test, deploy hoặc vận hành hệ thống bằng cùng một ngôn ngữ thay vì chỉ dựa vào tool cụ thể.

## Output / Artifact nên có

- Decision note hoặc config liên quan tới Model Routing
- Test/checklist/metric nếu concept nằm trên critical path
- Runbook hoặc debug note nếu có impact production

## Decision Checklist / Câu hỏi kiểm tra

- Model Routing giải quyết constraint cụ thể nào?
- Owner, boundary và rollback path có rõ không?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng Model Routing sai boundary làm debug hoặc design lệch hướng
- Thiếu metric/test khiến lỗi chỉ lộ khi scale, deploy hoặc tích hợp thật
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu Model Routing nếu hệ thống nhỏ và chưa chạm constraint liên quan
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI and ML Engineering
- Backend Engineering
- Data Engineering
- Security Attack Patterns

## Keywords / Từ khóa tìm kiếm

- Model Routing
- model routing
- model routing design
- model routing debugging
- model routing production
- model routing best practice

## Source trace

- OpenAI documentation
- Google Machine Learning Crash Course
- Designing Machine Learning Systems
- Anthropic prompt engineering docs
