# Feature Engineering

Aliases: Feature Engineering, feature engineering, feature extraction, thiết kế đặc trưng

Type: AI and ML Engineering

## Context / Ngữ cảnh

Feature Engineering là node bổ sung cho ComputingWiki về quá trình biến dữ liệu thô thành feature hữu ích cho model.

## Boundary / Ranh giới

### Nó là gì

Feature Engineering dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới quá trình biến dữ liệu thô thành feature hữu ích cho model.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Feature Engineering là hiểu boundary, input/output, state và failure mode riêng của quá trình biến dữ liệu thô thành feature hữu ích cho model.

## Project Role / Vai trò trong dự án

Feature Engineering giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Feature Engineering experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Feature Engineering ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Feature Engineering làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Feature Engineering nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Feature Store]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Feature Engineering
- [[Training Data]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Feature Engineering

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Feature Engineering
- feature engineering
- feature extraction
- thiết kế đặc trưng
- feature
- engineering

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
