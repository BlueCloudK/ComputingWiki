# Groundedness

Aliases: Groundedness, grounded response

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Groundedness xuất hiện khi AI output cần dựa trên source, retrieved context, tool result hoặc dữ liệu đã được cung cấp thay vì tự suy diễn ngoài căn cứ.

## Boundary / Ranh giới

### Nó là gì

Groundedness là mức độ câu trả lời được neo vào evidence cụ thể và có thể truy ngược về nguồn hỗ trợ.

### Nó không phải là gì

Groundedness không đồng nghĩa với câu trả lời luôn đúng. Nếu source sai hoặc thiếu, answer có thể grounded nhưng vẫn không correct ngoài thực tế.

## Core Mechanism / Cơ chế lõi

Pipeline cung cấp evidence cho model, yêu cầu model trả lời trong phạm vi evidence, kiểm tra claim với source/citation và đánh dấu phần không đủ căn cứ nếu cần.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế RAG answer, citation verification, hallucination reduction, eval rubric hoặc guardrail yêu cầu model không trả lời ngoài tài liệu.

## Output / Artifact nên có

- Evidence/context list
- Claim-to-source mapping
- Citation rule
- Groundedness rubric/score
- Unsupported claim report

## Decision Checklist / Câu hỏi kiểm tra

- Answer claim nào dựa vào source nào?
- Source có đủ để support claim không?
- Có citation đúng đoạn/page không?
- Model có nói ngoài evidence không?
- Khi evidence thiếu, system có từ chối hoặc nêu uncertainty không?

## Failure Modes / Cách nó gây lỗi

- Answer có citation nhưng citation không support claim.
- Model trộn kiến thức ngoài context vào câu trả lời.
- Retrieved context thiếu nhưng model vẫn trả lời tự tin.
- Groundedness eval chỉ chấm bề mặt, không so từng claim.
- Prompt yêu cầu ngắn quá làm mất điều kiện/uncertainty quan trọng.

## Khi nào chưa cần hoặc dễ over-engineer

- Creative writing hoặc brainstorming không yêu cầu source-grounded strict.
- Không nên tuyên bố grounded nếu không có evidence trace và eval rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Faithfulness]] vì faithfulness đo answer có bám evidence không.
- [[RAG Evaluation]] vì groundedness là tiêu chí quan trọng của RAG.
- [[Vector Search]] vì retrieved evidence là đầu vào để answer grounded.
- [[Output Validation]] vì output có thể cần check citation/claim.

## Liên quan rộng

- Evidence-based answer
- Citation verification
- Hallucination reduction

## Keywords / Từ khóa tìm kiếm

- Groundedness
- grounded response
- evidence grounded answer
- citation grounding
- claim source mapping
- RAG groundedness
- groundedness debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
