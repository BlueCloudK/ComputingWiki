# Retriever Query

Aliases: Retriever Query, retrieval query

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Retriever Query xuất hiện trong RAG khi user question hoặc task input cần được chuyển thành truy vấn phù hợp để tìm đúng tài liệu/chunk.

## Boundary / Ranh giới

### Nó là gì

Retriever Query là query gửi vào retriever/vector search/keyword search để lấy candidate context cho LLM.

### Nó không phải là gì

Retriever Query không nhất thiết giống nguyên văn câu hỏi user. Query tốt có thể được rewrite, expand, filter hoặc tách nhiều subquery.

## Core Mechanism / Cơ chế lõi

Pipeline nhận user input, tạo query embedding hoặc keyword query, thêm filter metadata nếu cần, retrieve top-k candidate, rồi rerank hoặc chọn context đưa vào prompt.

## Project Role / Vai trò trong dự án

Dùng node này khi debug RAG không tìm đúng tài liệu, recall thấp, query mơ hồ, metadata filter sai hoặc context bị nhiễu.

## Output / Artifact nên có

- Query text/embedding input
- Metadata filter
- Top-k setting
- Retrieved candidate list
- Query rewrite/expansion note nếu có

## Decision Checklist / Câu hỏi kiểm tra

- Query có giữ đúng intent user không?
- Có cần rewrite hoặc split query không?
- Metadata filter có loại nhầm tài liệu không?
- Top-k có đủ recall không?
- Retrieved chunks có evidence cần thiết không?

## Failure Modes / Cách nó gây lỗi

- Query quá ngắn làm retrieve sai.
- Query rewrite đổi ý user.
- Metadata filter quá hẹp làm mất tài liệu đúng.
- Top-k quá thấp làm thiếu evidence.
- Query chứa nhiễu từ prompt/user làm search lệch.

## Khi nào chưa cần hoặc dễ over-engineer

- Corpus nhỏ có thể bắt đầu bằng direct query trước.
- Không nên thêm query rewrite phức tạp nếu lỗi nằm ở chunking/index/filter.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[RAG]] vì retriever query là đầu vào của retrieval trong RAG.
- [[Vector Database]] vì nhiều retriever query chạy trên vector DB.
- [[Chunking Strategy]] vì query tốt vẫn fail nếu chunk không phù hợp.
- [[RAG Evaluation]] vì eval cần log query và retrieved evidence.

## Liên quan rộng

- Query rewriting
- Hybrid search
- Retrieval recall

## Keywords / Từ khóa tìm kiếm

- Retriever Query
- retrieval query
- query rewrite
- query expansion
- metadata filter
- top-k retrieval
- retriever query debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
