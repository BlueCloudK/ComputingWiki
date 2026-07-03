# Data Leakage

Aliases: Data Leakage, data leakage, leakage ML, rò rỉ dữ liệu

Type: AI and ML Engineering

## Context / Ngữ cảnh

Data Leakage là node bổ sung cho ComputingWiki về lỗi khi thông tin từ tương lai/test set lọt vào training khiến metric giả cao.

## Boundary / Ranh giới

### Nó là gì

Data Leakage dùng để gọi đúng khái niệm khi thiết kế, debug hoặc vận hành phần liên quan tới lỗi khi thông tin từ tương lai/test set lọt vào training khiến metric giả cao.

### Nó không phải là gì

Nó không thay thế toàn bộ vùng AI and ML Engineering; nếu dùng như nhãn chung mà không chỉ ra behavior cụ thể thì dễ làm graph nhiễu.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của Data Leakage là hiểu boundary, input/output, state và failure mode riêng của lỗi khi thông tin từ tương lai/test set lọt vào training khiến metric giả cao.

## Project Role / Vai trò trong dự án

Data Leakage giúp team đặt tên đúng khi đọc tài liệu, review thiết kế, viết test hoặc xử lý incident liên quan.

## Output / Artifact nên có

- Data Leakage experiment/model/data note
- Metric hoặc eval result liên quan
- Versioning/lineage nếu ảnh hưởng production model

## Decision Checklist / Câu hỏi kiểm tra

- Data Leakage ảnh hưởng data, training, inference hay evaluation?
- Metric nào chứng minh model tốt hơn hoặc an toàn hơn?
- Có version, dataset và rollback path cho production không?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai Data Leakage làm model pass offline nhưng fail trên dữ liệu thật
- Thiếu eval/lineage khiến không truy ra nguyên nhân regression
- Tối ưu một metric làm hỏng behavior quan trọng khác

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quy trình nặng cho Data Leakage nếu chỉ prototype nội bộ
- Dễ over-engineer nếu thêm MLOps stack trước khi có model/data lifecycle thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Training Data]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Data Leakage
- [[Evaluation Metric]] vì liên quan trực tiếp tới cách hiểu hoặc áp dụng Data Leakage

## Liên quan rộng

- Machine learning system
- Model lifecycle
- AI product reliability

## Keywords / Từ khóa tìm kiếm

- Data Leakage
- data leakage
- leakage ML
- rò rỉ dữ liệu
- data
- leakage

## Source trace

- Google Machine Learning Crash Course
- Google Rules of Machine Learning
- Chip Huyen - Designing Machine Learning Systems
