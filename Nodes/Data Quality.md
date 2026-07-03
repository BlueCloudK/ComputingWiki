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

- [[Data Pipeline]] vì pipeline cần quality checks
- [[Data Warehouse]] vì warehouse metric phụ thuộc data quality

## Liên quan rộng

- Freshness
- Completeness

## Source trace

- Fundamentals of Data Engineering
