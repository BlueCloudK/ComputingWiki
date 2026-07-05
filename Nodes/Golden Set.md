# Golden Set

Aliases: Golden Set, golden evaluation set

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Golden Set xuất hiện khi AI/RAG system cần một bộ case chuẩn đã được review để đo regression, so sánh model/prompt/retriever và giữ chất lượng qua release.

## Boundary / Ranh giới

### Nó là gì

Golden Set là tập test/eval cases có input, expected behavior, label, rubric hoặc reference answer được xem là nguồn chuẩn tương đối cho evaluation.

### Nó không phải là gì

Golden Set không phải dữ liệu production dump ngẫu nhiên. Nó cần được chọn, làm sạch, gắn nhãn và bảo trì để đại diện failure mode quan trọng.

## Core Mechanism / Cơ chế lõi

Team chọn case từ production, synthetic test hoặc human review; gắn expected output/rubric/metadata; chạy pipeline mới trên set này và so với baseline để phát hiện regression.

## Project Role / Vai trò trong dự án

Dùng node này khi xây offline eval, prompt regression, RAG evaluation, safety test hoặc release gate cho AI app.

## Output / Artifact nên có

- Eval cases with IDs
- Expected answer/rubric
- Metadata slices
- Baseline score
- Change history/owner

## Decision Checklist / Câu hỏi kiểm tra

- Case đại diện failure mode nào?
- Expected output có được review không?
- Set có metadata để phân tích theo nhóm không?
- Có tránh leakage vào prompt/training không?
- Golden set được cập nhật khi product thay đổi không?

## Failure Modes / Cách nó gây lỗi

- Golden set quá nhỏ hoặc quá dễ.
- Expected answer cũ so với product/source mới.
- Overfit prompt vào golden set.
- Không có metadata nên không biết regression nằm ở nhóm nào.
- Case production nhạy cảm bị đưa vào eval không được xử lý privacy.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype rất sớm có thể bắt đầu bằng vài manual eval case.
- Không nên coi golden set là chân lý tuyệt đối nếu source và yêu cầu đang thay đổi nhanh.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Eval Dataset]] vì golden set là dataset eval đã được chuẩn hóa.
- [[Offline Evaluation]] vì golden set thường chạy offline trước release.
- [[Prompt Regression]] vì prompt change cần check golden cases.
- [[Human Evaluation]] vì nhiều golden label đến từ human review.

## Liên quan rộng

- Regression testing
- Reference answer
- Evaluation baseline

## Keywords / Từ khóa tìm kiếm

- Golden Set
- golden evaluation set
- eval cases
- reference answer
- baseline score
- regression eval
- golden set debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
