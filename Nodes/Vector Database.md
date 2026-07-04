# Vector Database

Aliases: vector DB, cơ sở dữ liệu vector

Type: AI / ML Engineering / Data

## Context / Ngữ cảnh

Vector Database xuất hiện khi embedding cần được lưu, index và tìm kiếm theo similarity với latency chấp nhận được. Nó thường dùng trong RAG, semantic search, recommendation, deduplication, image/text search và agent memory retrieval.

## Boundary / Ranh giới

### Nó là gì

Vector Database là database hoặc extension tối ưu cho lưu trữ vector embedding và truy vấn nearest neighbors theo metric như cosine, dot product hoặc Euclidean distance. Nó thường hỗ trợ ANN index, metadata filter, collection/namespace, upsert/delete vector và trả về top-k kết quả gần nhất.

### Nó không phải là gì

Vector Database không tự làm RAG tốt. Nếu embedding model, chunking, metadata, permission filter hoặc evaluation sai thì vector DB vẫn trả kết quả kém. Nó cũng không thay thế relational database cho dữ liệu giao dịch; vector DB tốt cho similarity search, không phải mọi query chính xác hoặc transaction phức tạp.

## Core Mechanism / Cơ chế lõi

Dữ liệu được embed thành vector, gắn metadata, rồi upsert vào index. Khi query tới, hệ thống embed query, tìm top-k vector gần nhất bằng exact search hoặc approximate nearest neighbor, áp metadata filter nếu có, rồi trả document/chunk/id/score. Index config tạo trade-off giữa recall, latency, memory và update cost.

## Project Role / Vai trò trong dự án

Vector Database ảnh hưởng trực tiếp tới retrieval quality, latency, cost và access control trong RAG/semantic search. Khi debug AI app, team phải biết collection nào chứa dữ liệu gì, embedding model version nào tạo vector, metadata filter có đúng quyền không, và top-k có chứa evidence cần thiết không.

## Output / Artifact nên có

- Vector schema: id, embedding dimension, metadata fields, text/source pointer, version
- Index config: metric, index type, top-k, namespace/collection, filtering rule
- Ingestion/upsert/delete/re-embed pipeline
- Retrieval eval: query, expected source, top-k recall, latency
- Permission/tenant filter strategy trước hoặc trong vector search
- Backup/export/rebuild plan cho index nếu phải re-embed

## Decision Checklist / Câu hỏi kiểm tra

- Vector dimension và distance metric có khớp embedding model không?
- Collection/index có phân tách tenant/project/data source đúng không?
- Metadata filter có enforce quyền truy cập trước khi context vào LLM không?
- Index config đang ưu tiên recall hay latency, và có đo bằng eval không?
- Khi đổi embedding model/chunking, có re-embed và version lại index không?
- Delete/update document có xóa vector cũ khỏi index không?
- Có cần hybrid search/reranking vì vector search một mình chưa đủ không?

## Failure Modes / Cách nó gây lỗi

- Embedding dimension/metric sai làm similarity score vô nghĩa hoặc query fail.
- Index ANN quá aggressive làm latency thấp nhưng miss evidence quan trọng.
- Metadata/tenant filter sai làm lộ tài liệu không thuộc quyền.
- Document update/delete nhưng vector cũ vẫn còn, khiến RAG trả dữ liệu stale.
- Đổi embedding model nhưng không re-embed toàn bộ collection làm vector không cùng không gian.
- Chỉ dùng vector search cho exact keyword/code/error id làm retrieval miss kết quả cần thiết.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset nhỏ có thể dùng in-memory search hoặc database extension đơn giản trước.
- Nếu bài toán chủ yếu exact lookup/filter, SQL/keyword search có thể phù hợp hơn vector DB riêng.
- Không nên chọn vector DB theo hype nếu chưa có eval top-k recall/latency và yêu cầu vận hành rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Embedding]] vì vector database lưu và truy vấn embedding vectors.
- [[RAG]] vì vector DB thường là retrieval layer trong RAG.
- [[Reranking]] vì reranking thường cải thiện kết quả sau vector search.
- [[Chunking Strategy]] vì chunking quyết định đơn vị dữ liệu được index.
- [[AI Evaluation]] vì retrieval cần eval để biết top-k có đúng evidence không.

## Liên quan rộng

- Semantic search
- Information retrieval
- ANN index
- AI memory
- Data governance

## Keywords / Từ khóa tìm kiếm

- Vector Database
- vector DB
- cơ sở dữ liệu vector
- vector index
- ANN index
- approximate nearest neighbor
- similarity search
- cosine similarity
- dot product
- metadata filter
- vector collection
- vector upsert
- vector delete
- top-k recall
- vector database debugging

## Source trace

- Pinecone documentation
- Milvus documentation
- pgvector documentation
