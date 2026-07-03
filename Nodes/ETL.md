# ETL

Aliases: Extract Transform Load, trích xuất biến đổi nạp dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

ETL xuất hiện khi dữ liệu từ source system cần được lấy ra, làm sạch/biến đổi và nạp vào nơi lưu trữ phục vụ phân tích hoặc downstream.

## Boundary / Ranh giới

### Nó là gì

ETL là pattern data processing gồm Extract, Transform và Load, thường dùng trong data warehouse hoặc reporting pipeline.

### Nó không phải là gì

Nó không phải mọi data pipeline, không phải business dashboard, và không đảm bảo data đúng nếu thiếu validation/lineage.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là tách rõ ba bước: lấy dữ liệu từ source, chuyển đổi theo schema/business rule, rồi nạp vào target có thể query.

## Project Role / Vai trò trong dự án

ETL giúp dữ liệu operational trở thành dữ liệu phân tích ổn định. Nó là nơi dễ sinh bug metric nếu transform rule không rõ hoặc source đổi schema.

## Output / Artifact nên có

- Extract source và schedule
- Transform rule/schema mapping
- Load target và validation checks

## Decision Checklist / Câu hỏi kiểm tra

- Source dữ liệu có đáng tin và có owner không?
- Transform rule có version/test không?
- Load là full refresh, incremental hay upsert?
- Schema drift được phát hiện thế nào?
- Có audit số dòng và chất lượng sau load không?

## Failure Modes / Cách nó gây lỗi

- Transform rule sai làm metric sai nhưng không crash
- Incremental load miss record hoặc duplicate record
- Source schema đổi làm job hỏng hoặc dữ liệu lệch
- Không có audit nên không biết load thiếu dữ liệu

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần ETL formal nếu chỉ có một export nhỏ dùng một lần
- Dễ over-engineer nếu dựng ETL trước khi biết consumer dữ liệu cần gì

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Pipeline]] vì ETL thường là một dạng pipeline
- [[Data Warehouse]] vì ETL thường nạp dữ liệu vào warehouse
- [[Encoding and Evolution]] vì schema/format thay đổi ảnh hưởng transform/load

## Liên quan rộng

- ELT
- Data cleaning
- Incremental loading

## Source trace

- Fundamentals of Data Engineering
- Designing Data-Intensive Applications
