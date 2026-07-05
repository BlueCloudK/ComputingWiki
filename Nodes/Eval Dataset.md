# Eval Dataset

Aliases: Eval Dataset, evaluation dataset

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Eval Dataset xuất hiện khi cần một tập case cố định để đo chất lượng model, prompt, RAG hoặc agent workflow theo thời gian.

## Boundary / Ranh giới

### Nó là gì

Eval Dataset là tập input, expected output, expected evidence, label, metadata hoặc rubric dùng để chạy evaluation lặp lại được.

### Nó không phải là gì

Eval Dataset không phải log thô chưa chọn lọc. Nếu dữ liệu không được làm sạch, version và gắn expected behavior, eval dễ gây kết luận sai.

## Core Mechanism / Cơ chế lõi

Team thu case từ production, bug report, synthetic scenario hoặc domain expert, chuẩn hóa thành record có input/output kỳ vọng, rồi version dataset để chạy offline eval và regression.

## Project Role / Vai trò trong dự án

Dùng node này khi xây benchmark nội bộ, guard regression, đo RAG retrieval, kiểm tra prompt/model change hoặc gom edge case từ incident.

## Output / Artifact nên có

- Dataset file/version
- Case schema
- Expected answer/evidence/rubric
- Metadata: source, difficulty, category, owner
- Split: smoke/full/regression nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Case này đại diện use case thật hay edge case quan trọng?
- Expected output/evidence có rõ không?
- Dataset có version không?
- Có case negative/adversarial không?
- Có tránh leak test answer vào prompt/context không?

## Failure Modes / Cách nó gây lỗi

- Dataset quá dễ làm score ảo.
- Expected answer mơ hồ làm judge bất ổn.
- Dataset stale không còn phản ánh production.
- Case trùng với training/demo prompt làm overfit.
- Không phân loại case nên khó biết regression nằm ở đâu.

## Khi nào chưa cần hoặc dễ over-engineer

- Ý tưởng mới chưa có use case thật có thể bắt đầu bằng 10-20 case thủ công.
- Không nên tạo dataset lớn trước khi schema và rubric rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Offline Evaluation]] vì offline eval cần dataset cố định.
- [[RAG Evaluation]] vì RAG eval cần expected evidence/source.
- [[Regression Test]] vì eval dataset là regression guard cho AI behavior.
- [[Data Quality]] vì dataset bẩn làm eval sai.

## Liên quan rộng

- Benchmark dataset
- Golden set
- Edge case library

## Keywords / Từ khóa tìm kiếm

- Eval Dataset
- evaluation dataset
- golden dataset
- eval case schema
- expected answer
- expected evidence
- LLM eval dataset
- eval dataset debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
