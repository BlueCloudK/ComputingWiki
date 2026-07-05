# Chunk Overlap

Aliases: Chunk Overlap, overlap tokens

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Chunk Overlap xuất hiện trong RAG khi tài liệu được cắt thành chunk và cần giữ một phần ngữ cảnh lặp lại giữa các chunk liền kề.

## Boundary / Ranh giới

### Nó là gì

Chunk Overlap là số lượng hoặc tỷ lệ text/token được lặp lại giữa hai chunk để tránh mất ý ở điểm cắt.

### Nó không phải là gì

Chunk Overlap không phải cách chữa mọi lỗi retrieval. Overlap quá lớn làm index phình, duplicate context và tăng nhiễu nếu chunking boundary sai.

## Core Mechanism / Cơ chế lõi

Chunker cắt document thành đoạn có size nhất định, rồi giữ lại một phần cuối chunk trước vào đầu chunk sau. Khi query retrieve một chunk, phần overlap giúp giữ câu/section bị cắt ngang.

## Project Role / Vai trò trong dự án

Dùng node này khi debug RAG thiếu context ở biên chunk, citation bị cắt, retrieval duplicate hoặc index size/cost tăng bất thường.

## Output / Artifact nên có

- Chunk size và overlap config
- Sample chunks trước/sau
- Duplicate context check
- Retrieval eval comparison
- Index size/cost note

## Decision Checklist / Câu hỏi kiểm tra

- Điểm cắt có thường làm mất context không?
- Overlap bao nhiêu là đủ cho document type này?
- Duplicate chunks có làm retriever nhiễu không?
- Index size tăng bao nhiêu?
- Eval có cải thiện sau khi đổi overlap không?

## Failure Modes / Cách nó gây lỗi

- Overlap bằng 0 làm mất ý ở biên chunk.
- Overlap quá lớn làm nhiều chunk gần trùng nhau.
- Retriever trả nhiều bản lặp thay vì evidence đa dạng.
- Cost embedding/storage tăng không đáng.
- Dùng overlap để che lỗi cần semantic chunking.

## Khi nào chưa cần hoặc dễ over-engineer

- Document ngắn hoặc chunk theo heading rõ có thể không cần overlap lớn.
- Không nên tăng overlap nếu lỗi thật nằm ở query rewrite, metadata filter hoặc reranking.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Chunking Strategy]] vì overlap là tham số trong chunking.
- [[Document Ingestion]] vì overlap được áp trong ingestion pipeline.
- [[RAG Evaluation]] vì đổi overlap cần đo lại recall/answer quality.
- [[Vector Database]] vì overlap ảnh hưởng số record được index.

## Liên quan rộng

- Token window
- Context boundary
- Duplicate retrieval

## Keywords / Từ khóa tìm kiếm

- Chunk Overlap
- overlap tokens
- RAG chunk overlap
- chunk boundary
- duplicate chunks
- chunking config
- chunk overlap debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
