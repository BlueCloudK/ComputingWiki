# Overfitting

Aliases: Overfitting, overfitting, quá khớp, generalization gap

Type: AI and ML Engineering

## Context / Ngữ cảnh

Overfitting là node bổ sung cho ComputingWiki về model học quá sát training data và generalize kém trên dữ liệu mới.

## Boundary / Ranh giới

### Nó là gì

Overfitting dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới model học quá sát training data và generalize kém trên dữ liệu mới.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Overfitting là hiểu boundary, input/output, state và failure mode riêng của model học quá sát training data và generalize kém trên dữ liệu mới.

## Project Role / Vai trò trong dự án

Overfitting giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Overfitting experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Overfitting ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Overfitting làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Overfitting nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Validation Set]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Overfitting
- [[Model Training]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Overfitting

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Overfitting
- overfitting
- quá khớp
- generalization gap

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
