# Data Lakehouse

Aliases: lakehouse, kiến trúc lakehouse

Type: Data / Database

## Context / Ngữ cảnh

Data Lakehouse xuất hiện khi muốn kết hợp storage linh hoạt của lake với quản lý bảng/transaction/schema giống warehouse.

## Boundary / Ranh giới

### Nó là gì

Data Lakehouse là kiến trúc data platform dùng object storage kèm table format/metadata để phục vụ analytics đáng tin hơn.

### Nó không phải là gì

Nó không phải chỉ rename data lake và không cần thiết nếu warehouse/lake riêng đã đủ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là table metadata, transaction log, schema evolution và query engine trên data lake storage.

## Project Role / Vai trò trong dự án

Node này hữu ích khi cần vừa raw/flexible vừa query/model có governance.

## Output / Artifact nên có

- Lakehouse architecture note
- Table format/catalog choice
- Schema evolution và transaction policy

## Decision Checklist / Câu hỏi kiểm tra

- Có cần lakehouse hay warehouse/lake riêng đủ?
- Table format xử lý schema evolution thế nào?
- Query engine và governance đã rõ chưa?

## Failure Modes / Cách nó gây lỗi

- Gọi data lake là lakehouse nhưng thiếu catalog/table metadata
- Transaction/schema evolution bị hiểu sai làm data corrupt
- Dựng lakehouse theo trend không có workload

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu data volume/use case nhỏ
- Dễ over-engineer nếu warehouse hiện tại đã đáp ứng tốt

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Lake]] vì lakehouse xây trên lake storage
- [[Data Warehouse]] vì lakehouse mượn semantics phân tích từ warehouse

## Liên quan rộng

- Delta/Iceberg/Hudi
- Table formats

## Keywords / Từ khóa tìm kiếm

- Data Lakehouse
- lakehouse architecture
- Delta Lake
- Apache Iceberg
- table format
- warehouse lake hybrid
- kiến trúc lakehouse

## Source trace

- Fundamentals of Data Engineering
