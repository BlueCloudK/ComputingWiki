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

- [[Data Lake]] vì lakehouse xây trên lake storage
- [[Data Warehouse]] vì lakehouse mượn semantics phân tích từ warehouse

## Liên quan rộng

- Delta/Iceberg/Hudi
- Table formats

## Source trace

- Fundamentals of Data Engineering
