# RAG

Aliases: Retrieval Augmented Generation, truy xuất tăng cường sinh

Type: AI / ML Engineering

## Context / Ngữ cảnh

RAG xuất hiện khi LLM cần trả lời dựa trên tài liệu riêng, dữ liệu mới hoặc knowledge không nằm ổn định trong model. Nó thường dùng trong chatbot tài liệu, search assistant, support bot, coding assistant, enterprise knowledge base và AI app cần citation/evidence.

## Boundary / Ranh giới

### Nó là gì

RAG là kiến trúc kết hợp retrieval và generation: hệ thống tìm các đoạn thông tin liên quan từ nguồn dữ liệu, đưa chúng vào context, rồi LLM sinh câu trả lời dựa trên context đó. Giá trị chính nằm ở retrieval quality, chunking, ranking, prompt assembly, citation và evaluation.

### Nó không phải là gì

RAG không phải fine-tuning và không tự làm model “biết” dữ liệu mãi mãi. RAG cũng không bảo đảm câu trả lời đúng nếu retrieval sai, chunk quá kém, context bị nhiễu, permission lọc sai hoặc model không bám evidence. Thêm vector database không tự động biến app thành RAG tốt.

## Core Mechanism / Cơ chế lõi

Pipeline RAG thường gồm ingest tài liệu, chunking, embedding/indexing, query rewriting nếu cần, retrieval, reranking, prompt/context assembly, generation và citation. Khi user hỏi, hệ thống chọn context liên quan, giới hạn theo quyền truy cập, đưa vào prompt, rồi kiểm tra câu trả lời có bám nguồn hay không.

## Project Role / Vai trò trong dự án

RAG ảnh hưởng tới data pipeline, search quality, permission model, latency, cost, evaluation và security. Khi build AI app, team phải quyết định nguồn dữ liệu nào được index, chunk ra sao, retrieve bao nhiêu, filter permission ở đâu, citation thế nào, và đo chất lượng bằng bộ câu hỏi/evidence nào.

## Output / Artifact nên có

- RAG architecture note: data source, ingest, index, retriever, reranker, prompt assembly
- Chunking/indexing strategy cho từng loại tài liệu
- Retrieval evaluation set: question, expected source, expected answer/evidence
- Permission/filtering rule cho document, tenant, user, role hoặc project
- Citation/evidence policy: khi nào phải cite, khi nào trả lời “không có nguồn”
- Latency/cost budget cho retrieval, reranking và generation

## Decision Checklist / Câu hỏi kiểm tra

- User question cần exact source/evidence hay chỉ cần kiến thức chung?
- Chunk size/overlap có phù hợp cấu trúc tài liệu không?
- Retrieval có trả đúng nguồn trong top-k không?
- Có reranking hoặc hybrid search khi embedding search không đủ không?
- Permission filter chạy trước retrieval, sau retrieval hay cả hai?
- Câu trả lời có cite đúng đoạn nguồn hay hallucinate ngoài context?
- Có eval set để đo retrieval recall, answer correctness và citation faithfulness không?

## Failure Modes / Cách nó gây lỗi

- Chunking sai làm mất context quan trọng, model trả lời thiếu hoặc sai.
- Retrieval trả tài liệu không liên quan nhưng model vẫn tự tin trả lời.
- Permission filter sai làm user thấy tài liệu không thuộc quyền.
- Context quá dài hoặc nhiều noise làm model bỏ qua evidence chính.
- Không có citation/eval nên hallucination bị phát hiện muộn.
- Retrieved document chứa prompt injection khiến model lộ dữ liệu hoặc làm theo instruction độc hại.

## Khi nào chưa cần hoặc dễ over-engineer

- Nếu câu hỏi chỉ dựa trên dữ liệu nhỏ, ổn định và có cấu trúc, SQL/query trực tiếp có thể tốt hơn RAG.
- Không nên thêm vector database nếu keyword search hoặc rule-based lookup đã đủ chính xác.
- Không nên xây pipeline ingest/rerank phức tạp trước khi có eval set chứng minh retrieval hiện tại yếu.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Embedding]] vì embedding thường dùng để index và search semantic chunks.
- [[Chunking Strategy]] vì chất lượng chunk ảnh hưởng trực tiếp retrieval và answer quality.
- [[Reranking]] vì reranker giúp chọn context tốt hơn sau retrieval ban đầu.
- [[Vector Database]] vì nhiều RAG system lưu embedding index trong vector database.
- [[Prompt Injection]] vì retrieved content là nguồn untrusted có thể chứa instruction độc hại.
- [[RAG Leakage]] vì permission/filter/citation sai có thể làm lộ tài liệu riêng.

## Liên quan rộng

- Information retrieval
- Search relevance
- Enterprise knowledge base
- AI evaluation
- Data governance

## Keywords / Từ khóa tìm kiếm

- RAG
- Retrieval Augmented Generation
- truy xuất tăng cường sinh
- retrieval pipeline
- document retrieval
- semantic search
- vector search
- chunking
- reranking
- citation grounding
- evidence-based answer
- RAG evaluation
- RAG hallucination
- RAG permission filtering
- RAG leakage

## Source trace

- OpenAI RAG guidance
- LangChain RAG documentation
- LlamaIndex RAG documentation
