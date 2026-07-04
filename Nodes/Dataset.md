# Dataset

Aliases: training dataset, tập dữ liệu

Type: AI / ML Engineering

## Context / Ngữ cảnh

Dataset xuất hiện khi AI/ML system cần dữ liệu để train, fine-tune, evaluate, validate hoặc benchmark behavior. Trong dự án thực tế, dataset không chỉ là file dữ liệu mà là asset có schema, nguồn gốc, phiên bản, split, label quality và giới hạn sử dụng.

## Boundary / Ranh giới

### Nó là gì

Dataset là tập dữ liệu có cấu trúc hoặc bán cấu trúc được dùng cho một mục tiêu cụ thể như training, validation, test, evaluation hoặc retrieval corpus. Dataset cần mô tả nguồn dữ liệu, schema, label, sampling, preprocessing, version và quyền sử dụng.

### Nó không phải là gì

Dataset không tự đồng nghĩa với “dữ liệu đúng”. Dữ liệu có thể bias, stale, duplicate, thiếu nhãn, leak target, sai phân phối hoặc không đại diện production. Dataset cũng không phải model; nó là input quyết định model/evaluator học và đo cái gì.

## Core Mechanism / Cơ chế lõi

Dataset được thu thập, làm sạch, chuẩn hóa, gán nhãn, chia split và version hóa. Chất lượng dataset phụ thuộc vào data provenance, schema consistency, label agreement, class distribution, leakage control và độ khớp với use case thật. Với AI app, dataset còn dùng để tạo eval set và regression test cho model/prompt/RAG.

## Project Role / Vai trò trong dự án

Dataset ảnh hưởng trực tiếp tới chất lượng model, evaluation, debugging và trust. Khi model trả sai, team phải kiểm tra dữ liệu training/eval có đại diện không, nhãn có đúng không, split có leak không, và metric có đo đúng behavior người dùng cần không.

## Output / Artifact nên có

- Dataset card hoặc data note: source, schema, license, collection method, limitation
- Data split: train/validation/test/eval, tránh leakage giữa split
- Labeling guideline và quality check nếu có human label
- Data version và changelog khi dataset thay đổi
- Data quality report: missing value, duplicate, class distribution, outlier, bias risk
- Evaluation set đại diện use case thật

## Decision Checklist / Câu hỏi kiểm tra

- Dataset dùng cho training, validation, test hay evaluation?
- Dữ liệu có nguồn gốc rõ và được phép dùng không?
- Schema/label có nhất quán giữa các version không?
- Train/test split có leak user, time, document hoặc target không?
- Distribution có giống production traffic không?
- Có duplicate hoặc near-duplicate làm metric ảo không?
- Dataset có chứa PII/secret hoặc dữ liệu nhạy cảm cần xử lý không?

## Failure Modes / Cách nó gây lỗi

- Label sai hoặc guideline mơ hồ làm model học target không ổn định.
- Data leakage giữa train/test làm metric cao giả.
- Dataset stale khiến model/eval không phản ánh production hiện tại.
- Sampling bias làm model tốt trên nhóm phổ biến nhưng fail nhóm hiếm.
- Schema thay đổi nhưng pipeline không biết, gây train/eval sai âm thầm.
- Dữ liệu nhạy cảm lọt vào dataset làm rủi ro privacy/compliance.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype ý tưởng có thể bắt đầu bằng dataset nhỏ, nhưng phải ghi rõ giới hạn.
- Không nên xây data platform phức tạp trước khi biết dataset nào ảnh hưởng metric/use case.
- Không nên tối ưu model khi lỗi thật nằm ở label, split hoặc data quality.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Training]] vì dataset là input chính cho quá trình train/fine-tune.
- [[AI Evaluation]] vì eval dataset quyết định hệ thống được đo bằng câu hỏi/tình huống nào.
- [[Data Quality]] vì chất lượng dataset quyết định độ tin cậy của model và metric.
- [[RAG]] vì corpus tài liệu trong RAG cũng cần quản lý như dataset về nguồn, version và quyền truy cập.

## Liên quan rộng

- Data governance
- Labeling workflow
- Model debugging
- Bias analysis

## Keywords / Từ khóa tìm kiếm

- Dataset
- training dataset
- tập dữ liệu
- evaluation dataset
- validation set
- test set
- data split
- data leakage
- label quality
- dataset version
- dataset card
- data provenance
- class distribution
- stale dataset
- dataset debugging

## Source trace

- Google ML Crash Course
- scikit-learn documentation
- TensorFlow data documentation
