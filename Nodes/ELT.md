# ELT

Aliases: Extract Load Transform, ELT, nạp rồi biến đổi dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

ELT xuất hiện khi dữ liệu được nạp vào warehouse/lake trước rồi transform trong engine phân tích.

## Boundary / Ranh giới

### Nó là gì

ELT là pattern Extract-Load-Transform, thường dùng với warehouse mạnh và SQL transform.

### Nó không phải là gì

Nó không phải ETL truyền thống và không tự giải quyết data quality.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là load raw/staged data trước, sau đó transform thành model phục vụ analytics.

## Project Role / Vai trò trong dự án

Node này giúp phân biệt nơi transform logic sống và cách kiểm soát lineage/quality.

## Output / Artifact nên có

- Raw/staging/transform model
- Warehouse transform SQL or job
- Data quality check after transform

## Decision Checklist / Câu hỏi kiểm tra

- Transform xảy ra sau load ở engine nào?
- Raw data retention và access control ra sao?
- Model downstream có lineage rõ không?

## Failure Modes / Cách nó gây lỗi

- Raw PII vào warehouse không kiểm soát
- Transform SQL ad hoc làm metric lệch
- Schema drift làm model fail muộn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ELT nếu ETL nhỏ rõ ràng đủ
- Dễ over-engineer nếu warehouse chưa có analytical use case

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ETL]] vì ELT là biến thể pipeline khác thứ tự transform/load
- [[Data Warehouse]] vì ELT thường chạy trong warehouse

## Liên quan rộng

- Analytics engineering
- SQL transforms

## Keywords / Từ khóa tìm kiếm

- ELT
- Extract Load Transform
- warehouse transformation
- load then transform
- analytics pipeline
- modern data stack
- nạp rồi biến đổi dữ liệu

## Source trace

- Fundamentals of Data Engineering
- dbt docs
