# ELT

Aliases: Extract Load Transform, ELT

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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[ETL]] vì ELT là biến thể pipeline khác thứ tự transform/load
- [[Data Warehouse]] vì ELT thường chạy trong warehouse

## Liên quan rộng

- Analytics engineering
- SQL transforms

## Source trace

- Fundamentals of Data Engineering
- dbt docs
