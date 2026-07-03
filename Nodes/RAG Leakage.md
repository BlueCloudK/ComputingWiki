# RAG Leakage

Aliases: retrieval leakage, RAG data leakage, rò rỉ dữ liệu RAG

Type: AI Security / RAG

## Context / Ngữ cảnh

RAG Leakage xảy ra khi hệ thống retrieval đưa tài liệu nhạy cảm, sai tenant, sai scope hoặc không phù hợp vào context cho model.

## Boundary / Ranh giới

### Nó là gì

Nó là failure mode ở boundary giữa retriever, permission filter, prompt assembly và model output.

### Nó không phải là gì

Nó không chỉ là hallucination; dữ liệu có thể là thật nhưng bị lộ sai người, sai scope hoặc sai mục đích.

## Core Mechanism / Cơ chế lõi

Retriever lấy chunk theo similarity hoặc metadata. Nếu access control, tenant filter, redaction hoặc citation policy yếu, context có thể chứa dữ liệu không được phép hiển thị.

## Project Role / Vai trò trong dự án

Node này giúp review RAG app trong môi trường có tài liệu nội bộ, khách hàng, workspace hoặc role permission khác nhau.

## Output / Artifact nên có

- Retrieval permission matrix
- Tenant/role filter test set
- Redaction và citation policy cho retrieved context

## Decision Checklist / Câu hỏi kiểm tra

- Retriever có filter theo user, tenant, role trước khi trả chunk không?
- Chunk có chứa secret/PII hoặc dữ liệu nội bộ không cần thiết không?
- Model có được phép quote nguyên văn retrieved text không?
- Eval có case hỏi chéo tenant hoặc hỏi dữ liệu không có quyền không?

## Failure Modes / Cách nó gây lỗi

- User A nhận đoạn tài liệu của tenant B
- Prompt injection trong retrieved document ép model tiết lộ context
- Citation lộ tên file/path nội bộ dù nội dung đã được che một phần

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần machinery phức tạp nếu corpus public và không có permission boundary
- Dễ over-engineer nếu thêm nhiều guardrail nhưng không test đúng tenant/role boundary

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[RAG]] vì leakage xảy ra trong pipeline retrieval-augmented generation
- [[Data Leakage]] vì rủi ro chính là dữ liệu bị đưa ra sai boundary
- [[Prompt Injection]] vì retrieved text có thể trở thành instruction độc hại

## Liên quan rộng

- AI security
- Retrieval permission
- Tenant isolation

## Keywords / Từ khóa tìm kiếm

- RAG Leakage
- retrieval leakage
- RAG data leakage
- tenant leakage
- retrieval permission
- poisoned context
- rò rỉ dữ liệu RAG
- lộ dữ liệu retrieval

## Source trace

- OWASP Top 10 for LLM Applications
- NIST AI Risk Management Framework
