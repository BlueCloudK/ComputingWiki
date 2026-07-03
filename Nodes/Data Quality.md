# Data Quality

Aliases: data quality, chất lượng dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

Data Quality xuất hiện khi dữ liệu cần đáng tin để quyết định, report, ML hoặc automation.

## Boundary / Ranh giới

### Nó là gì

Data Quality là mức dữ liệu thỏa expectation về completeness, validity, accuracy, freshness, uniqueness và consistency.

### Nó không phải là gì

Nó không phải dashboard đẹp và không tự có nếu pipeline chạy xanh.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là định nghĩa expectation, validate, monitor, alert và xử lý issue theo owner.

## Project Role / Vai trò trong dự án

Node này giúp tránh report sai hoặc model học từ dữ liệu hỏng.

## Output / Artifact nên có

- Data quality expectations
- Freshness/completeness/validity checks
- Owner và incident process cho bad data

## Decision Checklist / Câu hỏi kiểm tra

- Metric nào cần quality guarantee?
- Freshness/completeness threshold là gì?
- Ai xử lý khi check fail?

## Failure Modes / Cách nó gây lỗi

- Pipeline xanh nhưng dữ liệu sai
- Metric sai vì duplicate/null/outlier không kiểm tra
- Không có owner nên data issue kéo dài

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần formal quality suite cho dataset ít dùng
- Dễ over-engineer nếu check quá nhiều nhưng không gắn quyết định nào

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Pipeline]] vì pipeline cần quality checks
- [[Data Warehouse]] vì warehouse metric phụ thuộc data quality

## Liên quan rộng

- Freshness
- Completeness

## Keywords / Từ khóa tìm kiếm

- Data Quality
- chất lượng dữ liệu
- data
- quality
- Database
- dữ liệu
- chất lượng
- hệ thống dữ liệu

## Source trace

- Fundamentals of Data Engineering
