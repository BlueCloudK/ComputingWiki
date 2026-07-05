# Offline Evaluation

Aliases: Offline Evaluation, offline eval

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Offline Evaluation xuất hiện khi cần đánh giá model, prompt, retriever hoặc pipeline AI trên tập dữ liệu cố định trước khi đưa ra production.

## Boundary / Ranh giới

### Nó là gì

Offline Evaluation là eval chạy trên dataset có sẵn, không phụ thuộc traffic live. Nó giúp so sánh version hệ thống trong điều kiện lặp lại được.

### Nó không phải là gì

Offline Evaluation không thay thế online monitoring hoặc user feedback. Dataset cố định có thể bỏ sót case production mới.

## Core Mechanism / Cơ chế lõi

Pipeline chạy trên eval dataset, tạo prediction/answer/tool trace, tính metric hoặc judge score, rồi so sánh với baseline trước đó. Kết quả thường dùng làm gate trước merge/deploy.

## Project Role / Vai trò trong dự án

Dùng node này khi cần kiểm tra regression sau khi đổi model, prompt, index, chunking, retriever, tool policy hoặc output schema.

## Output / Artifact nên có

- Eval dataset version
- Baseline result
- Metric/judge rubric
- Regression diff report
- Failed case list để review thủ công

## Decision Checklist / Câu hỏi kiểm tra

- Dataset có version và owner không?
- Metric nào là pass/fail gate?
- Baseline là version nào?
- Eval có deterministic đủ không?
- Failed cases có được inspect không?

## Failure Modes / Cách nó gây lỗi

- Dataset cũ không còn đại diện production.
- Gate quá lỏng nên regression lọt qua.
- Judge không ổn định làm score nhiễu.
- Chỉ nhìn average score, bỏ qua critical failure.
- Không lưu baseline nên không biết tốt/xấu hơn.

## Khi nào chưa cần hoặc dễ over-engineer

- Demo nhỏ chưa có use case thật có thể dùng manual review trước.
- Không nên tự động hóa quá nhiều khi dataset chưa sạch.

## Gồm những gì

- [[Eval Dataset]]

## Nối mạnh

- [[AI Evaluation]] vì offline eval là một hình thức AI evaluation.
- [[RAG Evaluation]] vì RAG eval thường bắt đầu bằng offline dataset.
- [[Prompt Regression]] vì prompt change cần offline regression check.
- [[Model Regression]] vì model change cần so sánh offline trước rollout.
- [[CI]] vì offline eval có thể chạy như quality gate.

## Liên quan rộng

- Benchmarking
- Regression testing
- LLM app quality

## Keywords / Từ khóa tìm kiếm

- Offline Evaluation
- offline eval
- eval dataset
- baseline comparison
- regression diff
- LLM eval
- offline evaluation debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
