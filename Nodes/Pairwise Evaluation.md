# Pairwise Evaluation

Aliases: Pairwise Evaluation, pairwise eval

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Pairwise Evaluation xuất hiện khi cần so sánh hai output/model/prompt/retriever trên cùng một input để chọn phương án tốt hơn thay vì chỉ chấm điểm tuyệt đối.

## Boundary / Ranh giới

### Nó là gì

Pairwise Evaluation là phương pháp đưa hai kết quả A/B cho evaluator hoặc judge so sánh theo rubric và chọn winner/tie/loser.

### Nó không phải là gì

Pairwise Evaluation không tự nói hệ thống đã đạt chuẩn production. Nó chỉ cho biết phương án nào tốt hơn trên tập case và tiêu chí đã chọn.

## Core Mechanism / Cơ chế lõi

Cùng một eval case được chạy qua hai candidate. Evaluator nhìn input, context và output A/B, chấm theo rubric như correctness, helpfulness, faithfulness, safety hoặc preference, rồi tổng hợp win rate.

## Project Role / Vai trò trong dự án

Dùng node này khi chọn prompt/model mới, so retriever/reranker, đánh giá RAG answer hoặc giảm bias khi điểm số tuyệt đối khó ổn định.

## Output / Artifact nên có

- Candidate A/B definition
- Eval case list
- Pairwise rubric
- Win/tie/loss result
- Failure analysis by slice

## Decision Checklist / Câu hỏi kiểm tra

- A/B khác nhau ở điểm nào?
- Rubric chọn winner có rõ không?
- Output có được blind/randomize order không?
- Win rate có đủ sample không?
- Winner có tốt hơn theo failure mode quan trọng không?

## Failure Modes / Cách nó gây lỗi

- Judge bị bias theo vị trí A/B.
- Rubric mơ hồ làm evaluator chọn theo cảm giác.
- Win rate cao nhưng fail ở slice quan trọng.
- So sánh hai output đều kém nhưng vẫn chọn một winner.
- Chỉ nhìn aggregate, không đọc case thua.

## Khi nào chưa cần hoặc dễ over-engineer

- Một prompt/model duy nhất giai đoạn đầu có thể dùng manual review trước.
- Không nên dùng pairwise eval nếu cần absolute compliance/safety threshold rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Evaluation]] vì pairwise evaluation là một chiến lược eval.
- [[Human Evaluation]] vì human reviewer thường dùng pairwise comparison.
- [[Offline Evaluation]] vì pairwise eval thường chạy offline trên golden/eval set.
- [[Golden Set]] vì cần case ổn định để so sánh A/B.

## Liên quan rộng

- A/B comparison
- Preference evaluation
- Win rate

## Keywords / Từ khóa tìm kiếm

- Pairwise Evaluation
- pairwise eval
- A/B evaluation
- preference evaluation
- win rate
- human pairwise review
- pairwise evaluation debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
