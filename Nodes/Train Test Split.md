# Train Test Split

Aliases: Train Test Split, train test split, data split, chia dữ liệu

Type: AI and ML Engineering

## Context / Ngữ cảnh

Train Test Split là node bổ sung cho ComputingWiki về cách chia dataset thành train, validation và test để đánh giá model.

## Boundary / Ranh giới

### Nó là gì

Train Test Split dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới cách chia dataset thành train, validation và test để đánh giá model.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Train Test Split là hiểu boundary, input/output, state và failure mode riêng của cách chia dataset thành train, validation và test để đánh giá model.

## Project Role / Vai trò trong dự án

Train Test Split giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Train Test Split experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Train Test Split ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Train Test Split làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Train Test Split nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Training Data]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Train Test Split
- [[Test Set]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Train Test Split

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Train Test Split
- train test split
- data split
- chia dữ liệu
- train
- test
- split

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
