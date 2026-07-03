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

- [[Data Pipeline]] vì CDC thường là input của pipeline
- [[Stream Processing]] vì CDC thường tạo event stream liên tục

## Liên quan rộng

- Replication logs
- Data sync

## Source trace

- DDIA
- Fundamentals of Data Engineering
