# Model Serving

Aliases: Model Serving, model serving, serve model, phục vụ mô hình

Type: AI and ML Engineering

## Context / Ngữ cảnh

Model Serving là node bổ sung cho ComputingWiki về hạ tầng đưa model đã train vào inference cho user/service.

## Boundary / Ranh giới

### Nó là gì

Model Serving dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới hạ tầng đưa model đã train vào inference cho user/service.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Model Serving là hiểu boundary, input/output, state và failure mode riêng của hạ tầng đưa model đã train vào inference cho user/service.

## Project Role / Vai trò trong dự án

Model Serving giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Model Serving experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Model Serving ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Model Serving làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Model Serving nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Inference]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Model Serving
- [[Online Inference]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Model Serving

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Model Serving
- model serving
- serve model
- phục vụ mô hình
- model
- serving

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
