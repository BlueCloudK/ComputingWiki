# Document Ingestion

Aliases: Document Ingestion, data ingestion for RAG

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Document Ingestion xuất hiện khi tài liệu cần được đưa vào hệ thống RAG/search để parse, clean, chunk, embed, index và cập nhật metadata.

## Boundary / Ranh giới

### Nó là gì

Document Ingestion là pipeline biến file/source thô thành dữ liệu có thể truy xuất: text sạch, chunk, metadata, embedding và index record.

### Nó không phải là gì

Document Ingestion không chỉ là upload file. Nếu parse sai, metadata mất hoặc chunk sai, RAG sẽ retrieve sai dù model tốt.

## Core Mechanism / Cơ chế lõi

Pipeline nhận document từ source, parse nội dung, normalize text, extract metadata, chunk, tạo embedding, lưu vào vector/database và ghi trace version để re-index khi source đổi.

## Project Role / Vai trò trong dự án

Dùng node này khi debug tài liệu không tìm thấy, index stale, metadata sai, duplicate document hoặc ingestion fail trong RAG app.

## Output / Artifact nên có

- Ingestion source list
- Parser/cleaning rule
- Metadata schema
- Chunking config
- Index version/trace
- Failed ingestion log

## Decision Checklist / Câu hỏi kiểm tra

- Source document đến từ đâu?
- Parser có giữ đúng cấu trúc quan trọng không?
- Metadata nào cần cho filter/retrieval?
- Khi tài liệu đổi, re-index thế nào?
- Có detect duplicate/stale document không?

## Failure Modes / Cách nó gây lỗi

- Parser bỏ mất bảng/header quan trọng.
- Metadata thiếu làm filter sai.
- Chunking cắt mất ngữ cảnh.
- Index stale sau khi source đổi.
- Duplicate document làm retrieval nhiễu.

## Khi nào chưa cần hoặc dễ over-engineer

- Corpus nhỏ, ít đổi có thể ingest thủ công trước.
- Không nên xây pipeline phức tạp nếu source và schema chưa ổn định.

## Gồm những gì

- [[Chunking Strategy]]

## Nối mạnh

- [[RAG]] vì ingestion tạo corpus cho RAG retrieve.
- [[Vector Database]] vì ingestion thường ghi embedding vào vector DB.
- [[Data Quality]] vì dữ liệu ingest bẩn làm output sai.
- [[RAG Evaluation]] vì ingestion change cần eval lại retrieval/answer.

## Liên quan rộng

- ETL for AI
- Knowledge base indexing
- Metadata extraction

## Keywords / Từ khóa tìm kiếm

- Document Ingestion
- RAG ingestion
- document parsing
- metadata extraction
- embedding pipeline
- re-indexing
- document ingestion debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
