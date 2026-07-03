# Poisoned Knowledge Base

Aliases: knowledge base poisoning, poisoned corpus, poisoning tài liệu RAG

Type: AI Security / RAG

## Context / Ngữ cảnh

Poisoned Knowledge Base xảy ra khi corpus dùng cho search/RAG chứa tài liệu độc hại, sai lệch hoặc bị attacker chỉnh để ảnh hưởng output của model.

## Boundary / Ranh giới

### Nó là gì

Nó là supply-chain/data-quality failure ở layer ingestion, indexing, retrieval và prompt assembly.

### Nó không phải là gì

Nó không phải lỗi model tự bịa thuần túy; nguồn sai hoặc độc đã đi vào hệ thống retrieval.

## Core Mechanism / Cơ chế lõi

Attacker hoặc lỗi vận hành đưa nội dung độc vào knowledge base. Retriever sau đó chọn chunk đó vì similarity/metadata, khiến model dùng nó như context đáng tin.

## Project Role / Vai trò trong dự án

Node này giúp thiết kế review pipeline ingest tài liệu, source trust, provenance, moderation và eval cho hệ thống RAG/agent.

## Output / Artifact nên có

- Source allowlist và provenance record
- Ingestion review hoặc quarantine flow
- Eval set phát hiện instruction độc trong retrieved document

## Decision Checklist / Câu hỏi kiểm tra

- Knowledge base nhận tài liệu từ nguồn nào và ai được upload?
- Có phân biệt trusted source, user content và external content không?
- Retrieved chunk có thể chứa instruction giả mạo system/developer không?
- Có rollback hoặc re-index khi phát hiện corpus bị nhiễm không?

## Failure Modes / Cách nó gây lỗi

- Model làm theo instruction độc nằm trong tài liệu retrieved
- Search ưu tiên tài liệu sai vì metadata/ranking bị thao túng
- Không có provenance nên không biết output sai đến từ nguồn nào

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần quarantine phức tạp nếu corpus nhỏ, readonly và do team kiểm soát
- Dễ over-engineer nếu thêm pipeline security lớn nhưng không có nguồn dữ liệu bên ngoài

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Document Ingestion]] vì poisoning thường đi vào qua ingest pipeline
- [[Source Attribution]] vì provenance giúp truy ngược nguồn gây lỗi
- [[RAG Evaluation]] vì cần eval để phát hiện context độc hoặc sai

## Liên quan rộng

- RAG security
- Data governance
- Supply chain risk

## Keywords / Từ khóa tìm kiếm

- Poisoned Knowledge Base
- knowledge base poisoning
- poisoned corpus
- RAG poisoning
- malicious document
- source provenance
- poisoning tài liệu RAG
- dữ liệu độc trong knowledge base

## Source trace

- OWASP Top 10 for LLM Applications
- NIST AI Risk Management Framework
