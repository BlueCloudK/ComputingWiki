# Object Storage

Aliases: object store, lưu trữ object

Type: Data / Database

## Context / Ngữ cảnh

Object Storage xuất hiện khi cần lưu file/blob lớn, static asset, backup hoặc data lake object.

## Boundary / Ranh giới

### Nó là gì

Object Storage lưu dữ liệu dạng object trong bucket/container với key và metadata.

### Nó không phải là gì

Nó không phải file system POSIX đầy đủ và không phải database transaction.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là put/get/list object qua API, durability cao, lifecycle policy và access control.

## Project Role / Vai trò trong dự án

Node này giúp lưu asset, backup, export và data lake với cost/durability tốt.

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

- [[Data Lake]] vì lake thường dùng object storage
- [[Backup]] vì backup hay lưu vào object storage

## Liên quan rộng

- Blob storage
- Static assets

## Source trace

- AWS Well-Architected
- Cloud docs
