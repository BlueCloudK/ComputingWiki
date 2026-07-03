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

- Bucket/key naming convention
- Access/lifecycle/retention policy
- Encryption và public-access setting

## Decision Checklist / Câu hỏi kiểm tra

- Object có cần public không?
- Retention/lifecycle theo data class nào?
- Có PII/secret trong object không?

## Failure Modes / Cách nó gây lỗi

- Bucket public ngoài ý muốn
- Lifecycle thiếu làm storage cost phình
- Dùng object storage như DB transactional

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu dữ liệu nhỏ và cần transaction trong DB
- Dễ over-engineer nếu tạo lake/blob layer không có use case

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
