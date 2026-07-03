# Model Registry

Aliases: Model Registry, model registry, model versioning, registry mô hình

Type: AI and ML Engineering

## Context / Ngữ cảnh

Model Registry là node bổ sung cho ComputingWiki về nơi quản lý version, metadata và lifecycle của model artifact.

## Boundary / Ranh giới

### Nó là gì

Model Registry dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới nơi quản lý version, metadata và lifecycle của model artifact.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Model Registry là hiểu boundary, input/output, state và failure mode riêng của nơi quản lý version, metadata và lifecycle của model artifact.

## Project Role / Vai trò trong dự án

Model Registry giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Model Registry experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Model Registry ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Model Registry làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Model Registry nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Model Serving]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Model Registry
- [[MLOps]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Model Registry

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Model Registry
- model registry
- model versioning
- registry mô hình
- model
- registry

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
