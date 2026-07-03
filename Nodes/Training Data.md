# Training Data

Aliases: Training Data, training data, train set, dữ liệu huấn luyện

Type: AI and ML Engineering

## Context / Ngữ cảnh

Training Data là node bổ sung cho ComputingWiki về dữ liệu dùng để model học parameter.

## Boundary / Ranh giới

### Nó là gì

Training Data dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới dữ liệu dùng để model học parameter.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Training Data là hiểu boundary, input/output, state và failure mode riêng của dữ liệu dùng để model học parameter.

## Project Role / Vai trò trong dự án

Training Data giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Training Data experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Training Data ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Training Data làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Training Data nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dataset]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Training Data
- [[Train Test Split]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Training Data

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Training Data
- training data
- train set
- dữ liệu huấn luyện
- training
- data

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
