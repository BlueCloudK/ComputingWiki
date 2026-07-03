# AI RAG and Agent Engineering

Aliases: RAG engineering, agent engineering, LLM application engineering, kỹ nghệ ứng dụng AI

Type: MOC

## Context / Ngữ cảnh

AI RAG and Agent Engineering là vùng kiến thức về LLM app, retrieval, tool use, agent workflow, evaluation, guardrails và production reliability.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC điều hướng cho các node thuộc AI / RAG / Agent Engineering.

### Nó không phải là gì

Nó không phải tutorial dài hoặc danh sách tool rời rạc; mục tiêu là map khái niệm để đi tiếp trong graph.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom node theo boundary, workflow, artifact, failure mode và operational signal.

## Project Role / Vai trò trong dự án

MOC này giúp chọn node cần đọc khi thiết kế, debug, deploy hoặc audit một phần hệ thống.

## Output / Artifact nên có

- Pack map
- Navigation links
- Source trace cấp vùng

## Decision Checklist / Câu hỏi kiểm tra

- Node mới có thuộc pack này thật không?
- Node đó có source trace và boundary rõ không?
- Link có giúp navigation hay chỉ làm graph nhiễu?

## Failure Modes / Cách nó gây lỗi

- Pack quá rộng làm người đọc không biết đi đâu
- Link quá nhiều làm graph nhiễu
- Node quá tool-specific nhưng không có cơ chế ổn định phía sau

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần chia sâu hơn nếu node chưa được dùng trong path hoặc project workflow
- Dễ over-engineer nếu biến MOC thành course hoặc tutorial

## Gồm những gì

- [[LLM Application]]
- [[System Prompt]]
- [[Developer Prompt]]
- [[User Prompt]]
- [[Prompt Template]]
- [[Prompt Versioning]]
- [[Prompt Registry]]
- [[Prompt Variable]]
- [[Prompt Context]]
- [[Instruction Hierarchy]]
- [[Tool Calling]]
- [[Function Calling]]
- [[Tool Schema]]
- [[Tool Permission]]
- [[Tool Result]]
- [[Tool Error]]
- [[Tool Timeout]]
- [[Tool Retry]]
- [[Tool Choice]]
- [[Tool Sandbox]]
- [[AI Agent]]
- [[Agent Loop]]
- [[Planning Loop]]
- [[Reflection Loop]]
- [[Agent Memory]]
- [[Short Term Memory]]
- [[Long Term Memory]]
- [[Conversation Memory]]
- [[Memory Retrieval]]
- [[Memory Compaction]]
- [[RAG Pipeline]]
- [[Document Ingestion]]
- [[Document Parser]]
- [[Text Extraction]]
- [[Chunking Strategy]]
- [[Chunk Size]]
- [[Chunk Overlap]]
- [[Metadata Extraction]]
- [[Embedding Model]]
- [[Embedding Dimension]]
- [[Vector Store]]
- [[Vector Search]]
- [[Hybrid Search]]
- [[Keyword Search]]
- [[Semantic Search]]
- [[Reranking]]
- [[Cross Encoder Reranker]]
- [[Retriever]]
- [[Retriever Query]]
- [[Context Assembly]]
- [[Context Compression]]
- [[Citation Grounding]]
- [[Source Attribution]]
- [[Answer Grounding]]
- [[Groundedness]]
- [[Retrieval Precision]]
- [[Retrieval Recall]]
- [[Retrieval Evaluation]]
- [[RAG Evaluation]]
- [[RAGAS]]
- [[Eval Dataset]]
- [[Golden Set]]
- [[Test Prompt Set]]
- [[LLM Judge]]
- [[Human Evaluation]]
- [[Pairwise Evaluation]]
- [[Rubric]]
- [[Evaluation Harness]]
- [[Offline Evaluation]]
- [[Online Evaluation]]
- [[Hallucination]]
- [[Hallucination Rate]]
- [[Faithfulness]]
- [[Answer Relevance]]
- [[Toxicity Evaluation]]
- [[Safety Evaluation]]
- [[Bias Evaluation]]
- [[Model Regression]]
- [[Prompt Regression]]
- [[Eval Drift]]
- [[Guardrail]]
- [[Input Guardrail]]
- [[Output Guardrail]]
- [[Output Validation]]
- [[Structured Output]]
- [[JSON Schema Output]]
- [[Constrained Decoding]]
- [[Refusal Policy]]
- [[Content Filter]]
- [[Policy Check]]
- [[Prompt Injection Defense]]
- [[Jailbreak]]
- [[Data Exfiltration via Prompt]]
- [[Indirect Prompt Injection]]
- [[Tool Abuse]]
- [[Human in the Loop]]
- [[Escalation Policy]]
- [[AI Audit Log]]
- [[Model Routing]]
- [[Fallback Model]]

## Nối mạnh

- [[AI and ML Engineering]] vì liên quan trực tiếp tới AI RAG and Agent Engineering
- [[Backend Engineering]] vì liên quan trực tiếp tới AI RAG and Agent Engineering
- [[Data Engineering]] vì liên quan trực tiếp tới AI RAG and Agent Engineering
- [[Security Attack Patterns]] vì liên quan trực tiếp tới AI RAG and Agent Engineering

## Liên quan rộng

- ComputingWiki expansion pack
- Project-oriented knowledge graph

## Keywords / Từ khóa tìm kiếm

- AI RAG and Agent Engineering
- RAG engineering
- agent engineering
- LLM application engineering
- kỹ nghệ ứng dụng AI

## Source trace

- OpenAI documentation
- Google Machine Learning Crash Course
- Designing Machine Learning Systems
- Anthropic prompt engineering docs
