# CDC

Aliases: Change Data Capture, bắt thay đổi dữ liệu

Type: Data / Database

## Context / Ngữ cảnh

CDC xuất hiện khi downstream cần biết thay đổi từ database/source gần realtime mà không scan toàn bộ.

## Boundary / Ranh giới

### Nó là gì

CDC là kỹ thuật capture insert/update/delete từ log, trigger hoặc timestamp để phát event/change stream.

### Nó không phải là gì

Nó không phải backup và không tự đảm bảo business event đúng nghĩa.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đọc change log hoặc detect delta, publish/change apply tới pipeline downstream.

## Project Role / Vai trò trong dự án

Node này giúp sync search index, warehouse, cache hoặc microservice data projection.

## Output / Artifact nên có

- CDC source và capture method
- Offset/checkpoint rule
- Schema-change và ordering handling

## Decision Checklist / Câu hỏi kiểm tra

- CDC lấy từ log, trigger hay polling?
- Consumer xử lý duplicate/out-of-order thế nào?
- Schema change được publish và test ra sao?

## Failure Modes / Cách nó gây lỗi

- Out-of-order update làm projection sai
- Offset commit sai làm mất hoặc duplicate event
- Schema drift làm consumer vỡ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần CDC nếu batch refresh đủ
- Dễ over-engineer nếu business không cần near-real-time sync

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Data Pipeline]] vì CDC thường là input của pipeline
- [[Stream Processing]] vì CDC thường tạo event stream liên tục

## Liên quan rộng

- Replication logs
- Data sync

## Keywords / Từ khóa tìm kiếm

- CDC
- Change Data Capture
- database change log
- incremental sync
- change stream
- replication feed
- bắt thay đổi dữ liệu

## Source trace

- DDIA
- Fundamentals of Data Engineering
