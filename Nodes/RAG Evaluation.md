# RAG Evaluation

Aliases: RAG Evaluation, retrieval augmented generation evaluation

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

RAG Evaluation xuất hiện khi cần biết hệ thống RAG trả lời đúng nhờ truy xuất đúng tài liệu, dùng evidence đúng và không bịa ngoài context.

## Boundary / Ranh giới

### Nó là gì

RAG Evaluation là quá trình đo chất lượng retrieval, grounding, citation, answer correctness và failure mode của pipeline RAG.

### Nó không phải là gì

RAG Evaluation không chỉ là hỏi thử vài câu trong chat. Nếu không có dataset, expected evidence và metric, kết quả rất dễ cảm tính.

## Core Mechanism / Cơ chế lõi

Hệ thống chạy tập câu hỏi kiểm thử qua pipeline retrieve → rerank/context → generate → validate. Kết quả được so với expected answer, expected source, citation và rule về hallucination/safety.

## Project Role / Vai trò trong dự án

Dùng node này khi nâng chất lượng chatbot/RAG app, chọn chunking, đổi embedding, thêm reranker hoặc kiểm tra regression sau khi cập nhật knowledge base.

## Output / Artifact nên có

- Eval dataset
- Retrieval metrics
- Answer quality rubric
- Citation/evidence check
- Regression report theo version pipeline

## Decision Checklist / Câu hỏi kiểm tra

- Câu hỏi eval có đại diện use case thật không?
- Có expected evidence/source không?
- Metric tách retrieval và generation chưa?
- Có kiểm tra hallucination/citation sai không?
- Kết quả có so sánh theo version pipeline không?

## Failure Modes / Cách nó gây lỗi

- Chỉ đo answer đẹp nhưng không đo retrieval.
- Dataset quá nhỏ hoặc quá dễ.
- Expected evidence thiếu nên không biết model có dùng đúng nguồn không.
- Dùng judge không ổn định nhưng không review sample.
- Eval không chạy lại sau đổi index/chunk/prompt.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype cực sớm có thể dùng manual eval nhỏ trước.
- Không nên xây framework eval lớn khi chưa có câu hỏi thật và failure mode rõ.

## Gồm những gì

- [[Eval Dataset]]
- [[Offline Evaluation]]

## Nối mạnh

- [[RAG]] vì RAG Evaluation đo chất lượng pipeline RAG.
- [[Retriever Query]] vì query truy xuất ảnh hưởng trực tiếp recall.
- [[Chunking Strategy]] vì chunking làm thay đổi evidence được retrieve.
- [[Prompt Regression]] vì prompt đổi có thể làm output RAG regress.
- [[Output Validation]] vì RAG output cần validate grounding/citation.

## Liên quan rộng

- Grounded answer quality
- Retrieval metrics
- LLM evaluation
- Production RAG reliability

## Keywords / Từ khóa tìm kiếm

- RAG Evaluation
- RAG eval
- retrieval evaluation
- grounded answer evaluation
- citation accuracy
- hallucination check
- RAG regression
- RAG evaluation debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
