# Agent Memory

Aliases: Agent Memory, agent memory, Memory

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Agent Memory xuất hiện khi AI agent cần lưu và dùng lại thông tin qua nhiều turn, nhiều task hoặc nhiều phiên làm việc. Nó thường liên quan tới user preference, project state, tool result, conversation summary, retrieved knowledge, long-term facts hoặc working memory trong một workflow.

## Boundary / Ranh giới

### Nó là gì

Agent Memory là lớp state mà agent có thể đọc/ghi để duy trì context ngoài prompt hiện tại. Memory có thể là short-term memory trong session, long-term memory qua database/vector store, episodic memory từ lịch sử task, hoặc structured memory như profile, checklist, plan và artifact state.

### Nó không phải là gì

Agent Memory không phải context window đơn thuần và không phải nơi nhét mọi log. Memory cũng không tự động đúng: nếu lưu sai, stale, quá riêng tư hoặc không có cơ chế retrieve/forget, agent có thể quyết định sai, leak dữ liệu hoặc bị nhiễu bởi thông tin cũ.

## Core Mechanism / Cơ chế lõi

Memory thường có pipeline: capture thông tin, quyết định có lưu không, ghi vào store, index/tag, retrieve khi task cần, rồi inject một phần vào context. Thiết kế memory tốt cần scope, TTL, ownership, privacy, retrieval quality, conflict resolution và audit trail cho việc agent đã dùng memory nào.

## Project Role / Vai trò trong dự án

Agent Memory ảnh hưởng tới độ hữu ích, tính nhất quán, bảo mật và khả năng debug của AI agent. Khi build agent production, team phải quyết định memory nào được lưu, ai được đọc, khi nào quên, memory có được user sửa/xóa không, và cách chứng minh output bị ảnh hưởng bởi memory nào.

## Output / Artifact nên có

- Memory schema: loại memory, owner, scope, TTL, sensitivity, source
- Read/write policy: agent được tự ghi gì, cần approval gì, user sửa/xóa thế nào
- Retrieval rule: khi nào query memory, top-k/priority, conflict resolution
- Audit/log: memory nào được dùng trong run nào
- Test case cho stale memory, conflicting memory, privacy leak và irrelevant retrieval

## Decision Checklist / Câu hỏi kiểm tra

- Memory này là session, project, user profile hay global knowledge?
- Agent có quyền tự lưu memory không, hay cần user/approval?
- Memory có chứa PII, secret, business data hoặc nội dung nhạy cảm không?
- Khi memory cũ mâu thuẫn memory mới, rule nào thắng?
- Có TTL/forget/delete mechanism không?
- Retrieval memory có thể kéo thông tin không liên quan vào prompt không?
- Có log để biết câu trả lời đã dùng memory nào không?

## Failure Modes / Cách nó gây lỗi

- Stale memory khiến agent làm theo quyết định cũ dù context hiện tại đã đổi.
- Memory scope sai làm dữ liệu của user/project này leak sang user/project khác.
- Agent lưu thông tin nhạy cảm không cần thiết và tạo rủi ro privacy/compliance.
- Retrieval kém kéo memory không liên quan vào context, làm output lệch.
- Memory conflict không được giải quyết làm agent hành xử không nhất quán.
- Không có audit khiến khó debug vì không biết model dựa vào memory nào.

## Khi nào chưa cần hoặc dễ over-engineer

- Chatbot một lượt hoặc workflow ngắn có thể dùng context hiện tại thay vì memory dài hạn.
- Không nên thêm vector memory trước khi biết loại thông tin nào cần nhớ và cách đánh giá retrieval.
- Không nên để agent tự ghi memory không giới hạn nếu chưa có policy, review và deletion path.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Agent]] vì memory thường là một thành phần giúp agent duy trì context qua nhiều bước.
- [[RAG]] vì long-term memory có thể dùng retrieval tương tự RAG.
- [[Vector Database]] vì memory semantic thường được index trong vector store.
- [[AI Evaluation]] vì memory behavior cần eval riêng cho stale/conflict/privacy cases.

## Liên quan rộng

- Personalization
- Context management
- Privacy engineering
- Agent observability

## Keywords / Từ khóa tìm kiếm

- Agent Memory
- agent memory
- Memory
- short term memory
- long term memory
- episodic memory
- working memory
- memory retrieval
- memory store
- stale memory
- memory conflict
- memory privacy
- agent context
- memory audit
- AI agent memory

## Source trace

- OpenAI documentation
- Anthropic prompt engineering documentation
- LangChain memory documentation
