# Recall

Aliases: Recall, recall, sensitivity, độ bao phủ

Type: AI and ML Engineering

## Context / Ngữ cảnh

Recall là node bổ sung cho ComputingWiki về tỷ lệ positive thật được model tìm ra.

## Boundary / Ranh giới

### Nó là gì

Recall dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới tỷ lệ positive thật được model tìm ra.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Recall là hiểu boundary, input/output, state và failure mode riêng của tỷ lệ positive thật được model tìm ra.

## Project Role / Vai trò trong dự án

Recall giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Recall experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Recall ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Recall làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Recall nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Confusion Matrix]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Recall

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Recall
- recall
- sensitivity
- độ bao phủ

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
