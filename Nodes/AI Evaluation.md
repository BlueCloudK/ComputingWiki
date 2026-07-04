# AI Evaluation

Aliases: AI Evaluation, LLM evaluation, Evaluation, đánh giá AI

Type: AI / ML Engineering

## Context / Ngữ cảnh

AI Evaluation xuất hiện khi output của model, RAG system hoặc agent cần được đo lường thay vì chỉ xem demo cảm tính. Nó thường dùng để quyết định prompt/model/retriever/tool workflow nào tốt hơn, phát hiện regression và kiểm soát chất lượng trước khi release.

## Boundary / Ranh giới

### Nó là gì

AI Evaluation là quá trình thiết kế test set, rubric, metric và review workflow để đo behavior của AI system. Nó có thể gồm automated eval, human review, LLM-as-judge, golden dataset, regression test, safety eval và production monitoring.

### Nó không phải là gì

AI Evaluation không phải một điểm số duy nhất chứng minh hệ thống “tốt”. Metric có thể lệch nếu dataset không đại diện, judge model bias, rubric mơ hồ hoặc test case quá ít. Eval cũng không thay thế observability production; nó là lớp kiểm tra trước/sau thay đổi.

## Core Mechanism / Cơ chế lõi

Eval bắt đầu từ use case và failure mode: chọn input đại diện, expected behavior/evidence, rubric chấm, metric aggregate và threshold release. Với LLM/RAG/agent, eval cần đo nhiều mặt như correctness, groundedness, retrieval quality, safety, tool use, latency, cost và regression theo version.

## Project Role / Vai trò trong dự án

AI Evaluation giúp team chuyển từ “cảm giác prompt này tốt” sang quyết định có bằng chứng. Khi thay model, prompt, chunking, retriever, tool policy hoặc memory, eval cho biết thay đổi đó cải thiện hay làm hỏng behavior nào.

## Output / Artifact nên có

- Eval dataset/golden set: input, expected answer/evidence, metadata, difficulty
- Rubric chấm: correctness, completeness, groundedness, safety, style, tool use
- Metric dashboard: pass rate, failure type, latency, cost, regression by version
- Judge configuration nếu dùng LLM-as-judge: prompt, model, calibration, sample review
- Error taxonomy và report top failure modes
- Release gate hoặc threshold cho thay đổi quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Eval đang đo behavior nào: answer quality, retrieval, safety, tool use hay latency/cost?
- Dataset có đại diện traffic thật và edge case quan trọng không?
- Expected answer/evidence có rõ để tránh chấm cảm tính không?
- Metric có bị gaming hoặc che failure nghiêm trọng không?
- LLM-as-judge có được calibrate bằng human review mẫu không?
- Eval có chạy lại khi đổi model/prompt/retriever/tool không?
- Failure được phân loại để biết sửa retrieval, prompt, policy hay data không?

## Failure Modes / Cách nó gây lỗi

- Eval set quá nhỏ hoặc quá dễ làm hệ thống pass nhưng fail với user thật.
- Rubric mơ hồ làm human/judge chấm không nhất quán.
- Judge model thiên vị hoặc bị prompt injection trong input làm điểm sai.
- Chỉ đo average score làm che lỗi nghiêm trọng ở nhóm case hiếm.
- Không version eval dataset khiến kết quả trước/sau không so được.
- Eval không gắn với release nên regression lọt vào production.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype rất sớm có thể bắt đầu bằng 20-50 case thủ công thay vì eval platform phức tạp.
- Không nên xây metric nhiều tầng trước khi xác định failure mode đáng sợ nhất.
- Không nên tin hoàn toàn LLM judge nếu không có sample human review và case calibration.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Dataset]] vì eval cần dataset/test set đại diện.
- [[RAG]] vì RAG cần eval retrieval và grounded answer riêng.
- [[AI Agent]] vì agent eval phải đo task success, tool use và safety.
- [[Regression Test]] vì eval thường dùng để bắt regression khi đổi model/prompt/pipeline.

## Liên quan rộng

- Model quality
- Human review
- Safety testing
- Production monitoring
- Error analysis

## Keywords / Từ khóa tìm kiếm

- AI Evaluation
- LLM evaluation
- Evaluation
- đánh giá AI
- eval dataset
- golden dataset
- LLM as judge
- eval rubric
- regression eval
- groundedness
- correctness metric
- tool use evaluation
- RAG evaluation
- agent evaluation
- AI regression testing

## Source trace

- OpenAI Evals documentation
- ML evaluation references
- Designing Machine Learning Systems
