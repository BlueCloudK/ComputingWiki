# Chunking Strategy

Aliases: Chunking Strategy, Chunking

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Chunking Strategy xuất hiện khi tài liệu cần được cắt thành đoạn phù hợp để embed, index và retrieve trong RAG/search.

## Boundary / Ranh giới

### Nó là gì

Chunking Strategy là cách chia document thành chunk dựa trên size, overlap, heading, semantic boundary, table/code block hoặc domain structure.

### Nó không phải là gì

Chunking Strategy không phải chỉ chọn một con số token size. Chunk tốt phải giữ context đủ cho retrieval và generation.

## Core Mechanism / Cơ chế lõi

Pipeline parse document, nhận diện boundary, cắt chunk, thêm metadata, có thể overlap hoặc hierarchy, rồi embed/index. Khi query retrieve chunk, context phải đủ để trả lời mà không kéo quá nhiều nhiễu.

## Project Role / Vai trò trong dự án

Dùng node này khi RAG retrieve thiếu ngữ cảnh, citation sai, table bị cắt hỏng, chunk quá dài/quá ngắn hoặc context window bị lãng phí.

## Output / Artifact nên có

- Chunk size/overlap config
- Boundary rule theo document type
- Metadata inherited từ document/section
- Sample chunk inspection
- Eval comparison theo strategy

## Decision Checklist / Câu hỏi kiểm tra

- Chunk có giữ đủ ý để trả lời không?
- Có cắt ngang bảng/code/list quan trọng không?
- Metadata section/document có được giữ không?
- Overlap có cần thiết không?
- Strategy mới có cải thiện eval không?

## Failure Modes / Cách nó gây lỗi

- Chunk quá nhỏ làm mất context.
- Chunk quá lớn làm retrieve nhiễu.
- Cắt ngang bảng/code làm evidence vô dụng.
- Metadata thiếu làm filter/citation sai.
- Overlap quá lớn làm index phình và duplicate context.

## Khi nào chưa cần hoặc dễ over-engineer

- Corpus nhỏ có thể bắt đầu với chunk đơn giản rồi eval.
- Không nên tối ưu chunking khi lỗi thật nằm ở query/filter/rerank.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Document Ingestion]] vì chunking nằm trong ingestion pipeline.
- [[RAG]] vì chunking ảnh hưởng trực tiếp context RAG.
- [[Vector Database]] vì chunk là record thường được embed/index.
- [[RAG Evaluation]] vì chunking change cần đo bằng eval.

## Liên quan rộng

- Text segmentation
- Semantic chunking
- Retrieval quality

## Keywords / Từ khóa tìm kiếm

- Chunking Strategy
- Chunking
- semantic chunking
- chunk size
- chunk overlap
- RAG chunking
- chunking debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
