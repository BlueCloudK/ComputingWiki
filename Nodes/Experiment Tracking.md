# Experiment Tracking

Aliases: Experiment Tracking, experiment tracking, ML experiment, theo dõi thí nghiệm

Type: AI and ML Engineering

## Context / Ngữ cảnh

Experiment Tracking là node bổ sung cho ComputingWiki về ghi lại config, dataset, metric và artifact của từng lần thử nghiệm.

## Boundary / Ranh giới

### Nó là gì

Experiment Tracking dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới ghi lại config, dataset, metric và artifact của từng lần thử nghiệm.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Experiment Tracking là hiểu boundary, input/output, state và failure mode riêng của ghi lại config, dataset, metric và artifact của từng lần thử nghiệm.

## Project Role / Vai trò trong dự án

Experiment Tracking giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Experiment Tracking experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Experiment Tracking ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Experiment Tracking làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Experiment Tracking nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Model Training]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Experiment Tracking
- [[Evaluation Metric]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Experiment Tracking

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Experiment Tracking
- experiment tracking
- ML experiment
- theo dõi thí nghiệm
- experiment
- tracking

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
