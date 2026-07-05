# Bias Evaluation

Aliases: Bias Evaluation, bias eval

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Bias Evaluation xuất hiện khi AI system cần được kiểm tra xem output có thiên lệch không công bằng giữa nhóm người, ngôn ngữ, dialect, domain hoặc use case khác nhau.

## Boundary / Ranh giới

### Nó là gì

Bias Evaluation là quá trình đo và review output AI theo nhóm/khía cạnh nhạy cảm hoặc phân khúc dữ liệu để phát hiện disparity, stereotype, underperformance hoặc harmful framing.

### Nó không phải là gì

Bias Evaluation không phải một điểm số chung duy nhất. Nếu chỉ nhìn average quality, lỗi thiên lệch theo nhóm nhỏ có thể bị che mất.

## Core Mechanism / Cơ chế lõi

Team tạo hoặc lấy eval cases có metadata nhóm, chạy model/pipeline, đo metric theo slice, dùng human review nếu cần và phân tích case có disparity để sửa data, prompt, model, policy hoặc product flow.

## Project Role / Vai trò trong dự án

Dùng node này khi đánh giá chatbot, classifier, recommender, RAG answer hoặc agent decision có tác động tới user khác nhau theo nhóm/context.

## Output / Artifact nên có

- Bias eval dataset with metadata slices
- Metric per group/slice
- Human review rubric nếu cần
- Failure case analysis
- Mitigation and re-eval plan

## Decision Checklist / Câu hỏi kiểm tra

- Nhóm/slice nào cần đo?
- Dataset có đủ đại diện không?
- Metric nào thể hiện unfair disparity?
- Có human review cho case nhạy cảm không?
- Fix xong có re-eval theo slice không?

## Failure Modes / Cách nó gây lỗi

- Dataset thiếu nhóm nhỏ nên bias không lộ.
- Chỉ đo aggregate score.
- Rubric human review mơ hồ.
- Fix bias ở một nhóm nhưng làm giảm quality nhóm khác.
- Không log metadata nên production không biết lỗi nằm ở slice nào.

## Khi nào chưa cần hoặc dễ over-engineer

- Demo nội bộ không tác động user thật có thể bắt đầu bằng checklist nhẹ.
- Không nên tuyên bố “không bias” nếu chưa định nghĩa nhóm, metric và giới hạn eval.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Evaluation]] vì bias evaluation là một nhánh eval quan trọng.
- [[Eval Dataset]] vì cần case có metadata group/slice.
- [[Human Evaluation]] vì bias/harmful framing thường cần human review.
- [[Safety Evaluation]] vì bias có thể là safety/product harm.

## Liên quan rộng

- Fairness testing
- Slice-based evaluation
- Harm analysis

## Keywords / Từ khóa tìm kiếm

- Bias Evaluation
- bias eval
- fairness evaluation
- slice evaluation
- disparity metric
- human review
- bias evaluation debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
