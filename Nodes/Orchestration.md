# Orchestration

Aliases: workflow orchestration, điều phối workflow

Type: Data / Database

## Context / Ngữ cảnh

Orchestration xuất hiện khi nhiều job/pipeline có dependency, schedule, retry và monitoring cần quản lý tập trung.

## Boundary / Ranh giới

### Nó là gì

Orchestration là điều phối thứ tự chạy, dependency, retry, state và alert của workflow.

### Nó không phải là gì

Nó không phải business orchestration chung và không tự sửa logic transform sai.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là DAG/workflow engine chạy task theo dependency và ghi trạng thái.

## Project Role / Vai trò trong dự án

Node này giúp data pipeline/release workflow rõ ràng và dễ retry/backfill hơn.

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

- [[Data Pipeline]] vì pipeline nhiều bước thường cần orchestration
- [[Backpressure]] vì workflow nhiều task cần kiểm soát overload/retry

## Liên quan rộng

- Airflow
- Workflow engine

## Source trace

- Apache Airflow docs
- Fundamentals of Data Engineering
