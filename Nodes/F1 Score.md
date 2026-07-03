# F1 Score

Aliases: F1 Score, F1 score, F-measure, điểm F1

Type: AI and ML Engineering

## Context / Ngữ cảnh

F1 Score là node bổ sung cho ComputingWiki về harmonic mean của precision và recall.

## Boundary / Ranh giới

### Nó là gì

F1 Score dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới harmonic mean của precision và recall.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của F1 Score là hiểu boundary, input/output, state và failure mode riêng của harmonic mean của precision và recall.

## Project Role / Vai trò trong dự án

F1 Score giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- F1 Score experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- F1 Score ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai F1 Score làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho F1 Score nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Precision]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng F1 Score
- [[Recall]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng F1 Score

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- F1 Score
- F1 score
- F-measure
- điểm F1
- score

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
