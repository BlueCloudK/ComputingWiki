# Elasticsearch

Aliases: Elasticsearch, Elastic Search, search engine

Type: Search / Data Store

## Context / Ngữ cảnh

Elasticsearch là distributed search and analytics engine dùng inverted index để tìm kiếm text, log, event và document.

## Boundary / Ranh giới

### Nó là gì

Nó là search engine cho full-text search, filtering, aggregation và near-real-time indexing trên document.

### Nó không phải là gì

Nó không phải database transaction chính cho dữ liệu nghiệp vụ cần consistency mạnh.

## Core Mechanism / Cơ chế lõi

Document được index vào shard, analyzer biến text thành token, inverted index giúp search nhanh, refresh interval quyết định độ trễ nhìn thấy dữ liệu mới.

## Project Role / Vai trò trong dự án

Node này giúp debug search relevance, mapping, analyzer, index lifecycle, ingestion lag và cluster health.

## Output / Artifact nên có

- Index mapping và analyzer config
- Search query/relevance test set
- Index lifecycle và retention policy

## Decision Checklist / Câu hỏi kiểm tra

- Field mapping có đúng type và analyzer không?
- Search cần exact match hay full-text relevance?
- Dữ liệu mới có cần search ngay hay chấp nhận near-real-time?
- Retention và shard sizing có phù hợp volume không?

## Failure Modes / Cách nó gây lỗi

- Mapping sai làm search/filter trả kết quả lệch
- Shard quá nhiều hoặc quá lớn làm cluster chậm
- Dùng làm source of truth khiến consistency với database chính bị lệch

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần Elasticsearch nếu database full-text search đủ đáp ứng
- Dễ over-engineer nếu thêm cluster search trước khi có nhu cầu relevance/analytics rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Index]] vì inverted index là cơ chế index trung tâm của search engine
- [[Observability]] vì Elasticsearch thường xuất hiện trong logging/search pipeline

## Liên quan rộng

- Full-text search
- Log analytics
- Search relevance

## Keywords / Từ khóa tìm kiếm

- Elasticsearch
- Elastic Search
- search engine
- inverted index
- index mapping
- analyzer
- shard
- search relevance

## Source trace

- Elasticsearch official documentation
