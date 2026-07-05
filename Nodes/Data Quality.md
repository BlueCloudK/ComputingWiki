# Data Quality

Aliases: data quality, chất lượng dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

Data Quality xuất hiện khi dữ liệu cần đáng tin để report, quyết định sản phẩm, billing, ML training, AI evaluation, automation hoặc migration. Pipeline chạy xanh không đủ; dữ liệu vẫn có thể thiếu, trễ, sai schema, duplicate, stale, lệch định nghĩa hoặc bị corrupt.

## Boundary / Ranh giới

### Nó là gì

Data Quality là mức dữ liệu thỏa expectation đã định nghĩa: completeness, validity, accuracy, freshness, uniqueness, consistency và timeliness. Nó biến “dữ liệu đúng” thành rule đo được, có owner, alert và cách xử lý khi rule fail.

### Nó không phải là gì

Data Quality không phải dashboard đẹp hoặc cảm giác “pipeline không lỗi”. Nó cũng không chỉ là validation lúc nhập liệu; dữ liệu có thể hỏng trong transform, join, backfill, migration, cache, replication hoặc manual fix. Quality cần được kiểm tra ở nơi dữ liệu được dùng để ra quyết định.

## Core Mechanism / Cơ chế lõi

Team định nghĩa expectation cho dataset/field/metric, chạy checks như null rate, uniqueness, schema, range, referential consistency, freshness, volume anomaly và distribution drift. Khi check fail, hệ thống alert owner, chặn publish/deploy nếu cần, hoặc mở incident/data issue để sửa nguồn hoặc backfill.

## Project Role / Vai trò trong dự án

Data Quality là node cần mở khi report sai, model học từ dữ liệu bẩn, RAG/eval dùng corpus lỗi, metric sản phẩm lệch hoặc migration/backfill có rủi ro. Nó giúp team phân biệt lỗi pipeline chạy fail và lỗi pipeline chạy thành công nhưng tạo data sai.

## Output / Artifact nên có

- Data quality expectations: field/rule/threshold/owner
- Checks: completeness, validity, uniqueness, freshness, consistency, distribution
- Data issue runbook: detect, quarantine, backfill, republish, notify consumer
- Dashboard/alert cho freshness, volume anomaly, null/duplicate rate, schema drift
- Contract hoặc documentation cho metric/dataset quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Dataset/metric này dùng để quyết định gì?
- Field nào bắt buộc, unique, enum/range hoặc không được null?
- Freshness/completeness threshold là bao nhiêu?
- Có check schema drift, duplicate, referential consistency và outlier không?
- Khi check fail, có block publish/model training/report không?
- Ai là owner sửa bad data và thông báo consumer?
- Có backfill/rollback plan nếu dữ liệu sai đã được publish không?

## Failure Modes / Cách nó gây lỗi

- Pipeline xanh nhưng dữ liệu sai do join key, timezone hoặc dedup logic sai.
- Metric sai vì duplicate/null/outlier không được kiểm tra.
- Dataset stale nhưng dashboard/model vẫn dùng như dữ liệu mới.
- Schema drift làm downstream silently drop field hoặc parse sai.
- Không có owner nên data issue kéo dài và consumer tự vá riêng.
- Data leakage vào training/evaluation làm model score cao giả.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset ít dùng, không ảnh hưởng quyết định quan trọng có thể bắt đầu với check nhẹ.
- Không nên check mọi field nếu không ai hành động khi fail.
- Không nên xây quality platform phức tạp trước khi có expectation và owner rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Pipeline]] vì pipeline cần quality checks trước khi publish dữ liệu.
- [[Data Warehouse]] vì warehouse metric phụ thuộc data quality.
- [[Dataset]] vì training/evaluation dataset cần kiểm tra leakage, label và freshness.
- [[AI Evaluation]] vì eval sai dữ liệu làm kết quả đánh giá sai.
- [[Validation]] vì validation là một lớp kiểm tra rule dữ liệu ở boundary.

## Liên quan rộng

- Freshness
- Completeness
- Data governance
- Metric correctness

## Keywords / Từ khóa tìm kiếm

- Data Quality
- data quality
- chất lượng dữ liệu
- data validation
- freshness check
- completeness check
- accuracy check
- uniqueness check
- consistency check
- schema drift
- data contract
- bad data detection
- null rate
- duplicate data
- data quality debugging

## Source trace

- Fundamentals of Data Engineering
- Data quality engineering references
