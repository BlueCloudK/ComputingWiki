# Human Evaluation

Aliases: Human Evaluation, human eval

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Human Evaluation xuất hiện khi chất lượng AI output không thể đo đủ bằng metric tự động và cần người đánh giá theo rubric rõ.

## Boundary / Ranh giới

### Nó là gì

Human Evaluation là quá trình reviewer/domain expert chấm hoặc so sánh output AI dựa trên tiêu chí như correctness, usefulness, grounding, tone, safety hoặc task success.

### Nó không phải là gì

Human Evaluation không phải cảm nhận ngẫu nhiên. Nếu thiếu rubric, sampling và agreement check, kết quả dễ bị thiên lệch và khó lặp lại.

## Core Mechanism / Cơ chế lõi

Team chọn sample case, ẩn hoặc random hóa output nếu cần, đưa rubric cho evaluator, thu score/comment, kiểm tra disagreement và chuyển insight thành eval dataset, prompt/model fix hoặc policy change.

## Project Role / Vai trò trong dự án

Dùng node này khi đánh giá chatbot/RAG/agent, kiểm tra output khó đo tự động, review failed cases hoặc tạo golden set cho offline evaluation.

## Output / Artifact nên có

- Evaluation rubric
- Sample selection rule
- Reviewer instruction
- Score/comment dataset
- Disagreement/failure analysis

## Decision Checklist / Câu hỏi kiểm tra

- Tiêu chí chấm có rõ không?
- Reviewer có đủ domain context không?
- Sample có đại diện production không?
- Có blind comparison nếu so model/prompt không?
- Kết quả có được đưa vào eval dataset không?

## Failure Modes / Cách nó gây lỗi

- Rubric mơ hồ làm mỗi người chấm một kiểu.
- Sample quá nhỏ hoặc cherry-pick.
- Reviewer biết model nào nên bị bias.
- Chỉ lấy average score, không đọc failure comment.
- Kết quả human eval không được chuyển thành action.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype rất sớm có thể dùng manual review nhẹ.
- Không nên mở human eval lớn khi rubric và use case chưa rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Evaluation]] vì human evaluation là một nhánh AI evaluation.
- [[Eval Dataset]] vì human review tốt có thể tạo golden dataset.
- [[Offline Evaluation]] vì human-labeled cases thường dùng cho offline eval.
- [[RAG Evaluation]] vì grounding/citation đôi khi cần human review.

## Liên quan rộng

- Rubric
- Domain expert review
- Pairwise comparison
- Labeling quality

## Keywords / Từ khóa tìm kiếm

- Human Evaluation
- human eval
- AI human review
- evaluation rubric
- pairwise comparison
- evaluator agreement
- human evaluation debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
