# Data Warehouse

Aliases: analytical warehouse, kho dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

Data Warehouse xuất hiện khi tổ chức cần lưu dữ liệu đã tổ chức để phân tích, reporting, BI hoặc decision support.

## Boundary / Ranh giới

### Nó là gì

Data Warehouse là hệ thống lưu trữ dữ liệu phân tích được tối ưu cho query đọc, mô hình hóa metric/dimension và lịch sử dữ liệu.

### Nó không phải là gì

Nó không phải database transaction chính của app, không phải data lake raw, và không tự đảm bảo metric đúng nếu model/ETL sai.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom dữ liệu từ nhiều source, chuẩn hóa/mô hình hóa, lưu ở dạng query được và phục vụ analytics với freshness/quality rõ.

## Project Role / Vai trò trong dự án

Warehouse giúp team tránh mỗi dashboard tự join dữ liệu khác nhau. Nó tạo nơi thống nhất cho metric, reporting và analytical queries.

## Output / Artifact nên có

- Warehouse schema/model
- Metric/dimension definitions
- Freshness và data quality checks

## Decision Checklist / Câu hỏi kiểm tra

- Warehouse phục vụ report/BI/use case nào?
- Grain của bảng fact/dimension là gì?
- Metric có definition thống nhất không?
- Freshness cần realtime, hourly hay daily?
- Source lineage và owner có rõ không?

## Failure Modes / Cách nó gây lỗi

- Metric khác nhau giữa dashboard vì model không thống nhất
- Warehouse dùng như OLTP làm query/write pattern sai
- Data stale nhưng không có freshness alert
- Transform thiếu lineage làm không truy được nguồn sai

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần warehouse nếu analytics còn rất ít và source đơn giản
- Dễ over-engineer nếu dựng model tổng quát trước khi có câu hỏi phân tích thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ETL]] vì ETL thường chuẩn bị dữ liệu cho warehouse
- [[Data Pipeline]] vì warehouse cần pipeline ingest/refresh ổn định
- [[SQL]] vì warehouse thường được query bằng SQL hoặc SQL-like language

## Liên quan rộng

- BI
- Dimensional modeling
- Metrics layer

## Source trace

- Fundamentals of Data Engineering
- Designing Data-Intensive Applications
