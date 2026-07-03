# Precision

Aliases: Precision, precision, positive predictive value, độ chính xác dương

Type: AI and ML Engineering

## Context / Ngữ cảnh

Precision là node bổ sung cho ComputingWiki về tỷ lệ prediction positive là đúng trong các positive được model dự đoán.

## Boundary / Ranh giới

### Nó là gì

Precision dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới tỷ lệ prediction positive là đúng trong các positive được model dự đoán.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Precision là hiểu boundary, input/output, state và failure mode riêng của tỷ lệ prediction positive là đúng trong các positive được model dự đoán.

## Project Role / Vai trò trong dự án

Precision giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Precision experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Precision ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Precision làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Precision nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Confusion Matrix]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Precision

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Precision
- precision
- positive predictive value
- độ chính xác dương

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
