# Data Engineering

Aliases: data pipelines, kỹ thuật dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

Data Engineering xuất hiện khi dữ liệu cần được thu thập, chuyển đổi, kiểm tra chất lượng và phục vụ cho analytics, reporting, ML hoặc hệ thống downstream.

## Boundary / Ranh giới

### Nó là gì

Data Engineering là vùng xây dựng data pipeline, batch/stream processing, warehouse/lake và data quality để dữ liệu dùng lại được.

### Nó không phải là gì

Nó không chỉ là database CRUD, không phải dashboard, và không thay thế domain modeling của ứng dụng chính.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là data flow: ingest, validate, transform, store, serve và monitor. Mỗi bước cần rõ source, schema, freshness, ownership và failure handling.

## Project Role / Vai trò trong dự án

Vùng này giúp dữ liệu không bị biến thành file rời rạc hoặc query thủ công. Nó tạo đường đi đáng tin từ event/source system tới nơi dùng dữ liệu.

## Output / Artifact nên có

- Data pipeline hoặc lineage note
- Schema, freshness và quality expectation
- Recovery/backfill plan cho pipeline quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Source dữ liệu là gì và ai sở hữu?
- Dữ liệu cần batch, stream hay cả hai?
- Schema thay đổi thì downstream bị ảnh hưởng thế nào?
- Freshness và quality requirement là gì?
- Pipeline fail thì retry, backfill hay alert ra sao?

## Failure Modes / Cách nó gây lỗi

- Pipeline silently fail làm report/ML dùng dữ liệu cũ
- Schema drift làm downstream vỡ bất ngờ
- Không có lineage nên không biết metric đến từ đâu
- Transform logic nằm trong query ad hoc khó kiểm soát

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần data platform nếu chỉ có vài query thủ công ít rủi ro
- Dễ over-engineer nếu dựng lake/warehouse trước khi có use case dữ liệu rõ

## Gồm những gì

- [[Data Pipeline]]
- [[ETL]]
- [[Data Warehouse]]
- [[Data Lake]]
- [[ELT]]
- [[Data Lakehouse]]
- [[CDC]]
- [[Data Quality]]
- [[Orchestration]]

## Nối mạnh

- [[Batch Processing]] vì nhiều pipeline xử lý dữ liệu theo lô
- [[Stream Processing]] vì pipeline realtime cần xử lý event liên tục
- [[Encoding and Evolution]] vì schema/format thay đổi ảnh hưởng downstream

## Liên quan rộng

- Analytics engineering
- Data quality
- Data governance
- Machine learning data

## Keywords / Từ khóa tìm kiếm

- Data Engineering
- data pipelines
- kỹ thuật dữ liệu
- data
- engineering
- Database
- dữ liệu
- kỹ thuật
- mục lục kiến thức
- nhánh kiến thức

## Source trace

- Designing Data-Intensive Applications
- Fundamentals of Data Engineering
