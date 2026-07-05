# Vector Store

Aliases: Vector Store, vector storage

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Vector Store xuất hiện khi RAG/semantic search cần lưu embedding vector cùng document/chunk metadata để query bằng vector search.

## Boundary / Ranh giới

### Nó là gì

Vector Store là storage layer lưu vector embedding, id, payload/metadata và đôi khi cả raw text/chunk để phục vụ similarity search hoặc retrieval.

### Nó không phải là gì

Vector Store không tự thay thế database nghiệp vụ hay authorization layer. Nó chỉ là retrieval/index layer và vẫn cần metadata, permission filter, backup và eval.

## Core Mechanism / Cơ chế lõi

Ingestion tạo embedding cho chunk/document rồi upsert vào vector store. Query được embed, chạy nearest-neighbor search với filter/ranking, trả về candidate context cho RAG hoặc search UI.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế RAG indexing, debug retrieval sai, chọn vector database, quản lý metadata/filter, reindex embedding hoặc kiểm soát cost/storage.

## Output / Artifact nên có

- Collection/index schema
- Embedding model/dimension
- Metadata fields and filters
- Upsert/delete/reindex procedure
- Retrieval eval and backup note

## Decision Checklist / Câu hỏi kiểm tra

- Vector store lưu text hay chỉ id + metadata?
- Embedding dimension/model có cố định không?
- Metadata filter nào bắt buộc cho permission/source?
- Reindex khi đổi embedding model ra sao?
- Có backup/delete/retention policy không?

## Failure Modes / Cách nó gây lỗi

- Đổi embedding model nhưng không reindex toàn bộ.
- Metadata thiếu làm filter permission/citation sai.
- Delete document nhưng vector cũ còn trong index.
- Vector store drift với source database.
- Chỉ tối ưu top-k mà không eval recall/faithfulness.

## Khi nào chưa cần hoặc dễ over-engineer

- Corpus nhỏ hoặc structured lookup có thể dùng keyword/SQL trước.
- Không nên dùng vector store như source of truth cho dữ liệu nghiệp vụ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Vector Database]] vì vector database là implementation phổ biến của vector store.
- [[Vector Search]] vì vector store phục vụ vector search.
- [[Embedding]] vì dữ liệu chính là embedding vector.
- [[Document Ingestion]] vì ingestion tạo/upsert vector record.

## Liên quan rộng

- Semantic retrieval
- ANN index
- Reindexing

## Keywords / Từ khóa tìm kiếm

- Vector Store
- vector storage
- embedding store
- vector index
- vector metadata
- reindex embedding
- vector store debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
