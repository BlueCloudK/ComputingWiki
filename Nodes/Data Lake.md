# Data Lake

Aliases: raw data lake, hồ dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

Data Lake xuất hiện khi cần lưu nhiều loại dữ liệu ở dạng raw hoặc semi-structured để dùng lại cho analytics, ML, exploration hoặc downstream processing.

## Boundary / Ranh giới

### Nó là gì

Data Lake là storage layer lưu dữ liệu đa dạng với schema có thể áp dụng khi đọc hoặc khi transform sang layer khác.

### Nó không phải là gì

Nó không phải nơi đổ dữ liệu vô tổ chức, không thay thế warehouse cho reporting chuẩn, và không có giá trị nếu thiếu catalog/quality/governance.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là lưu dữ liệu theo zone/layer, format và metadata để pipeline sau có thể đọc, transform, audit và quản lý lifecycle.

## Project Role / Vai trò trong dự án

Data Lake giúp giữ dữ liệu raw cho replay, exploration và ML, nhưng cần governance để không thành data swamp.

## Output / Artifact nên có

- Lake zone/layer convention
- Dataset catalog, owner và retention rule
- Format/schema và quality expectation

## Decision Checklist / Câu hỏi kiểm tra

- Dữ liệu nào cần giữ raw và vì sao?
- Dataset có owner, catalog và retention không?
- Format có phù hợp query/processing không?
- PII/security boundary được kiểm soát thế nào?
- Dữ liệu raw sẽ được transform sang layer nào?

## Failure Modes / Cách nó gây lỗi

- Data lake thành data swamp vì không có metadata/owner
- Raw PII bị lưu rộng không kiểm soát quyền
- Format nhỏ lẻ làm query/processing chậm
- Không có lifecycle policy làm storage cost tăng

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần data lake nếu chỉ có vài dataset nhỏ đã phục vụ tốt trong database/warehouse
- Dễ over-engineer nếu lưu mọi thứ raw mà không có use case replay/ML/analytics

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Pipeline]] vì lake cần pipeline ingest và transform
- [[Data Warehouse]] vì warehouse thường dùng dữ liệu đã transform từ lake/source
- [[Encoding and Evolution]] vì format/schema evolution rất quan trọng trong lake

## Liên quan rộng

- Object storage
- Data catalog
- Lakehouse
- Data governance

## Source trace

- Fundamentals of Data Engineering
- Designing Data-Intensive Applications
