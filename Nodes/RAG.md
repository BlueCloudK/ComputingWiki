# RAG

Aliases: Retrieval Augmented Generation, truy xuất tăng cường sinh

Type: AI / ML Engineering

## Context / Ngữ cảnh

RAG xuất hiện khi LLM cần dùng knowledge riêng hoặc tài liệu mới mà không chỉ dựa vào parametric memory.

## Boundary / Ranh giới

### Nó là gì

RAG là khái niệm dùng để gọi đúng phần việc, constraint hoặc failure mode liên quan trong hệ thống.

### Nó không phải là gì

Nó không phải nhãn để thêm cho đủ thuật ngữ; nếu không chỉ ra boundary, owner hoặc behavior cụ thể thì dễ làm graph rối mà không giúp debug/design.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi của RAG là retriever, chunking, embedding, reranking, prompt assembly và citation.

## Project Role / Vai trò trong dự án

RAG giúp team đọc code, thiết kế, debug hoặc vận hành bằng đúng ngôn ngữ thay vì gom mọi vấn đề vào một khái niệm quá rộng.

## Output / Artifact nên có

- RAG decision note hoặc checklist ngắn cho boundary đang dùng
- Config/test/metric liên quan trực tiếp tới RAG
- Failure note ghi rõ RAG ảnh hưởng user, runtime hay data thế nào

## Decision Checklist / Câu hỏi kiểm tra

- RAG đang nằm ở runtime, code, data, network hay operations boundary nào?
- Có metric, test, config hoặc diagram nào chứng minh behavior của RAG không?
- Khi RAG fail, user hoặc service nào bị ảnh hưởng trước?

## Failure Modes / Cách nó gây lỗi

- Dùng sai boundary của RAG làm team debug nhầm layer
- Thiếu test/metric/config nên lỗi chỉ lộ khi tích hợp hoặc chạy production
- Gọi đúng tên RAG nhưng không ghi rõ owner, constraint hoặc rollback path

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu RAG nếu hệ thống nhỏ và chưa có failure mode thật liên quan
- Dễ over-engineer nếu thêm tool/process quanh RAG trước khi có nhu cầu vận hành hoặc học tập rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- AI system design
- Model operations
- Data quality

## Keywords / Từ khóa tìm kiếm

- RAG
- Retrieval Augmented Generation
- truy xuất tăng cường sinh
- rag debugging
- rag design
- AI engineering
- ML system
- kỹ thuật AI

## Source trace

- OpenAI RAG guidance; LangChain docs
