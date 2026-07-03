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

- Workflow DAG
- Dependency, retry và backfill policy
- Task state/alerting config

## Decision Checklist / Câu hỏi kiểm tra

- Task nào phụ thuộc dữ liệu của task nào?
- Retry có idempotent không?
- Backfill có làm duplicate hoặc overwrite sai không?

## Failure Modes / Cách nó gây lỗi

- Dependency sai làm job chạy trên dữ liệu thiếu
- Retry không idempotent tạo duplicate
- Alert noise vì task không phân loại severity

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần orchestrator cho một job đơn giản
- Dễ over-engineer nếu DAG platform nặng hơn data flow thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Pipeline]] vì pipeline nhiều bước thường cần orchestration
- [[Backpressure]] vì workflow nhiều task cần kiểm soát overload/retry

## Liên quan rộng

- Airflow
- Workflow engine

## Keywords / Từ khóa tìm kiếm

- Orchestration
- workflow orchestration
- điều phối workflow
- Data
- Database
- dữ liệu
- hệ thống dữ liệu

## Source trace

- Apache Airflow docs
- Fundamentals of Data Engineering
