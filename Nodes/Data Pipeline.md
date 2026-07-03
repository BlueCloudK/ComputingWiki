# Data Pipeline

Aliases: data workflow, pipeline dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

Data Pipeline xuất hiện khi dữ liệu cần đi qua nhiều bước từ source tới nơi dùng: ingest, transform, validate, store và serve.

## Boundary / Ranh giới

### Nó là gì

Data Pipeline là chuỗi xử lý dữ liệu có dependency, schedule/trigger, input, output và failure handling rõ.

### Nó không phải là gì

Nó không phải một query thủ công, không phải dashboard, và không chỉ là moving data nếu không có quality/ownership.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là dataflow có kiểm soát: source, transformation, checkpoint, validation, retry, backfill và observability.

## Project Role / Vai trò trong dự án

Pipeline giúp dữ liệu production/analytics/ML có đường đi lặp lại được. Nó giảm phụ thuộc vào thao tác thủ công và giúp debug khi metric sai.

## Output / Artifact nên có

- Pipeline DAG hoặc flow note
- Source/target schema và ownership
- Retry, alert, backfill và data quality checks

## Decision Checklist / Câu hỏi kiểm tra

- Source và target của pipeline là gì?
- Pipeline chạy batch, stream hay event-triggered?
- Step nào transform dữ liệu và rule nằm ở đâu?
- Fail thì retry, skip, stop hay backfill?
- Freshness và quality được monitor thế nào?

## Failure Modes / Cách nó gây lỗi

- Pipeline fail silent làm dữ liệu cũ nhưng dashboard vẫn xanh
- Dependency không rõ làm job chạy sai thứ tự
- Backfill không có plan làm metric lịch sử lệch
- Transform logic phân tán khiến lineage mù

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần pipeline platform nếu dữ liệu nhỏ và cập nhật thủ công ít rủi ro
- Dễ over-engineer nếu tạo DAG phức tạp trước khi data flow ổn định

## Gồm những gì

- [[ETL]]

## Nối mạnh

- [[Batch Processing]] vì nhiều pipeline chạy theo batch/schedule
- [[Stream Processing]] vì pipeline realtime xử lý event liên tục
- [[Data Warehouse]] vì warehouse thường là target của pipeline analytics

## Liên quan rộng

- Data lineage
- Orchestration
- Data quality

## Keywords / Từ khóa tìm kiếm

- Data Pipeline
- data workflow
- batch pipeline
- stream pipeline
- data ingestion
- data transformation
- pipeline orchestration
- pipeline dữ liệu
- luồng xử lý dữ liệu

## Source trace

- Fundamentals of Data Engineering
- Designing Data-Intensive Applications
