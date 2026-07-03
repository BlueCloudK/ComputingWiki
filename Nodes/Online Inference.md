# Online Inference

Aliases: Online Inference, online inference, real-time inference, suy luận realtime

Type: AI and ML Engineering

## Context / Ngữ cảnh

Online Inference là node bổ sung cho ComputingWiki về chạy inference ngay khi request/user cần kết quả.

## Boundary / Ranh giới

### Nó là gì

Online Inference dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới chạy inference ngay khi request/user cần kết quả.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Online Inference là hiểu boundary, input/output, state và failure mode riêng của chạy inference ngay khi request/user cần kết quả.

## Project Role / Vai trò trong dự án

Online Inference giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Online Inference experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Online Inference ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Online Inference làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Online Inference nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Inference]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Online Inference
- [[Model Serving]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Online Inference

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Online Inference
- online inference
- real-time inference
- suy luận realtime
- online
- inference

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
