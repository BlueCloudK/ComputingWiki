# Embedding

Aliases: vector embedding, nhúng vector

Type: AI / ML Engineering

## Context / Ngữ cảnh

Embedding xuất hiện khi text, image, audio, code hoặc item cần được biểu diễn thành vector để so sánh semantic similarity, clustering, recommendation, retrieval hoặc search. Trong RAG, embedding thường dùng để index chunks và tìm nội dung gần nghĩa với query.

## Boundary / Ranh giới

### Nó là gì

Embedding là vector số học đại diện cho nội dung trong không gian nhiều chiều. Các item có ý nghĩa gần nhau thường có vector gần nhau theo metric như cosine similarity, dot product hoặc Euclidean distance. Embedding model quyết định cách nội dung được mã hóa.

### Nó không phải là gì

Embedding không phải ý nghĩa tuyệt đối và không bảo đảm câu trả lời đúng. Vector gần nhau chỉ nói về similarity theo model và dữ liệu huấn luyện. Embedding cũng không thay thế metadata filter, permission check, keyword search hoặc reranking khi bài toán cần exact match, quyền truy cập hoặc độ chính xác cao.

## Core Mechanism / Cơ chế lõi

Input được đưa qua embedding model để tạo vector có dimension cố định. Vector được lưu trong index/vector database và so sánh bằng distance metric. Chất lượng phụ thuộc vào model, preprocessing, chunking, normalization, distance metric, index config và độ khớp giữa query embedding với document embedding.

## Project Role / Vai trò trong dự án

Embedding ảnh hưởng trực tiếp tới search relevance, RAG retrieval, recommendation và semantic deduplication. Khi debug RAG, team phải kiểm tra embedding model có phù hợp ngôn ngữ/domain không, chunk có đủ context không, metric/index có đúng không và kết quả top-k có thực sự chứa evidence cần thiết không.

## Output / Artifact nên có

- Embedding model decision: model name, dimension, language/domain fit, cost/latency
- Preprocessing/chunking rule trước khi embed
- Vector index config: distance metric, normalization, index type, top-k
- Retrieval evaluation set để đo top-k recall/relevance
- Re-embedding plan khi đổi model, schema hoặc chunking strategy
- Metadata/permission filtering rule kết hợp với vector search

## Decision Checklist / Câu hỏi kiểm tra

- Embedding model có phù hợp ngôn ngữ, domain và loại dữ liệu không?
- Chunk/query được embed cùng model và cùng preprocessing không?
- Distance metric có khớp model recommendation không?
- Có cần hybrid search hoặc keyword filter cho exact term không?
- Permission/tenant filter được áp trước hay sau vector search?
- Khi đổi embedding model, có re-embed toàn bộ index không?
- Top-k retrieval có được đánh giá bằng câu hỏi/evidence thật không?

## Failure Modes / Cách nó gây lỗi

- Dùng model không hợp ngôn ngữ/domain làm retrieval trả kết quả gần nghĩa sai.
- Chunk quá dài/ngắn làm vector mất ý nghĩa hoặc thiếu context.
- Metric/index config sai làm similarity score không đáng tin.
- Không re-embed sau khi đổi model làm query vector và document vector không cùng không gian.
- Vector search không kèm permission filter làm lộ tài liệu không thuộc quyền.
- Chỉ dùng embedding search cho keyword exact như mã lỗi/API name làm miss kết quả cần thiết.

## Khi nào chưa cần hoặc dễ over-engineer

- Dataset nhỏ hoặc lookup exact field có thể dùng SQL/keyword search đơn giản hơn.
- Không nên thêm vector database nếu chưa có eval chứng minh semantic search cần thiết.
- Không nên tối ưu index ANN phức tạp trước khi retrieval quality cơ bản đã đúng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[RAG]] vì embedding thường là nền của retrieval trong RAG.
- [[Vector Database]] vì vector index thường được lưu và truy vấn trong vector database.
- [[Chunking Strategy]] vì chunking quyết định nội dung nào được biến thành vector.
- [[Reranking]] vì reranking thường cải thiện kết quả sau vector retrieval ban đầu.

## Liên quan rộng

- Semantic search
- Recommendation system
- Similarity search
- Information retrieval

## Keywords / Từ khóa tìm kiếm

- Embedding
- vector embedding
- nhúng vector
- semantic embedding
- embedding model
- vector dimension
- cosine similarity
- dot product
- distance metric
- vector search
- semantic search
- text embedding
- re-embedding
- embedding index
- retrieval embedding

## Source trace

- OpenAI embeddings documentation
- Sentence Transformers documentation
