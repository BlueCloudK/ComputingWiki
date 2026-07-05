# Faithfulness

Aliases: Faithfulness, answer faithfulness

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Faithfulness xuất hiện khi cần kiểm tra AI output có bám đúng vào context/source/tool result được cung cấp hay tự thêm thông tin không có căn cứ.

## Boundary / Ranh giới

### Nó là gì

Faithfulness là mức độ câu trả lời nhất quán với evidence/context đã cho, đặc biệt trong RAG hoặc tool-augmented AI.

### Nó không phải là gì

Faithfulness không đồng nghĩa với correctness tuyệt đối. Một answer có thể faithful với context nhưng context sai; hoặc đúng ngoài đời nhưng không faithful vì không được support bởi evidence đã đưa.

## Core Mechanism / Cơ chế lõi

Evaluator so sánh từng claim trong output với retrieved context/source/tool observation. Claim không được support, mâu thuẫn hoặc thêm thông tin ngoài evidence sẽ bị xem là faithfulness failure.

## Project Role / Vai trò trong dự án

Dùng node này khi đánh giá RAG answer, citation quality, hallucination, grounded response hoặc regression sau khi đổi retriever/prompt/model.

## Output / Artifact nên có

- Claim-to-evidence mapping
- Faithfulness score/rubric
- Unsupported claim list
- Source/context sample
- Regression cases

## Decision Checklist / Câu hỏi kiểm tra

- Claim nào trong answer cần evidence?
- Evidence có thật sự support claim không?
- Model có thêm thông tin ngoài context không?
- Citation có trỏ đúng đoạn không?
- Context sai hay model suy diễn sai?

## Failure Modes / Cách nó gây lỗi

- Answer nghe đúng nhưng không nằm trong source.
- Citation có nhưng không support claim.
- Context retrieved đúng nhưng model suy diễn quá đà.
- Metric chỉ chấm fluency nên bỏ sót unsupported claims.
- Prompt yêu cầu answer tự tin làm model che uncertainty.

## Khi nào chưa cần hoặc dễ over-engineer

- Task creative không yêu cầu grounded answer có thể không cần faithfulness strict.
- Không nên chỉ dùng LLM judge nếu claim/evidence quan trọng mà không có sample human review.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[RAG Evaluation]] vì faithfulness là metric chính của RAG answer.
- [[Groundedness]] vì cả hai cùng kiểm tra answer bám evidence.
- [[Hallucination Rate]] vì unsupported claim làm tăng hallucination.
- [[Human Evaluation]] vì faithfulness nhiều khi cần reviewer so claim với source.

## Liên quan rộng

- Claim verification
- Citation quality
- Grounded response

## Keywords / Từ khóa tìm kiếm

- Faithfulness
- answer faithfulness
- claim evidence
- unsupported claim
- RAG faithfulness
- citation verification
- faithfulness debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
