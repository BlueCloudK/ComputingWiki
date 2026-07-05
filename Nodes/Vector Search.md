# Vector Search

Aliases: Vector Search, semantic vector search

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Vector Search xuất hiện khi hệ thống cần tìm document/chunk/item gần nghĩa với query dựa trên embedding thay vì chỉ match keyword chính xác.

## Boundary / Ranh giới

### Nó là gì

Vector Search là kỹ thuật biến query và data thành vector embedding rồi tìm các vector gần nhau theo similarity/distance để phục vụ semantic retrieval.

### Nó không phải là gì

Vector Search không tự đảm bảo câu trả lời đúng. Retrieval có thể trả context gần nghĩa nhưng thiếu chính xác, thiếu quyền truy cập hoặc không đủ evidence.

## Core Mechanism / Cơ chế lõi

Pipeline tạo embedding cho document/chunk và lưu trong vector index. Khi có query, hệ thống embed query, tìm top-k vector gần nhất, có thể filter metadata/rerank rồi đưa kết quả cho RAG hoặc app.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế RAG retrieval, semantic search, hybrid search, vector database, chunking/evaluation hoặc debug vì sao search trả kết quả lệch.

## Output / Artifact nên có

- Embedding model and dimension
- Vector index config
- Similarity metric
- Metadata filter rule
- Retrieval eval: recall, precision, faithfulness impact

## Decision Checklist / Câu hỏi kiểm tra

- Embedding model có hợp domain/ngôn ngữ không?
- Chunk size/metadata có hỗ trợ retrieval không?
- Similarity metric và index config có đúng không?
- Top-k có đủ context nhưng không quá nhiễu không?
- Có filter permission/source/time không?

## Failure Modes / Cách nó gây lỗi

- Chunk sai làm vector search tìm đúng nghĩa nhưng thiếu context.
- Query embed không hợp domain/ngôn ngữ.
- Top-k quá cao đưa nhiều nhiễu vào prompt.
- Metadata filter thiếu làm lộ dữ liệu không đúng quyền.
- Không eval retrieval nên không biết lỗi nằm ở search hay generation.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset nhỏ/structured có thể dùng keyword/filter/SQL trước.
- Không nên dùng vector search thay thế permission model hoặc data quality pipeline.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Embedding]] vì vector search dựa trên embedding.
- [[Vector Database]] vì vector database lưu và query vector index.
- [[RAG]] vì vector search là retrieval path phổ biến của RAG.
- [[Groundedness]] vì retrieved evidence ảnh hưởng answer có grounded không.

## Liên quan rộng

- Semantic search
- Hybrid search
- ANN index

## Keywords / Từ khóa tìm kiếm

- Vector Search
- semantic vector search
- embedding search
- nearest neighbor search
- vector index
- hybrid search
- vector search debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
