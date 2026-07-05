# Model Regression

Aliases: Model Regression, model behavior regression

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Model Regression xuất hiện khi đổi model, model version, provider, quantization hoặc inference config làm chất lượng behavior giảm so với baseline.

## Boundary / Ranh giới

### Nó là gì

Model Regression là sự suy giảm behavior quan trọng sau thay đổi model hoặc cấu hình inference: accuracy, reasoning, format, latency, safety, tool use hoặc grounding.

### Nó không phải là gì

Model Regression không phải mọi khác biệt câu chữ. Chỉ coi là regression khi khác biệt phá contract, metric, user outcome hoặc guardrail.

## Core Mechanism / Cơ chế lõi

Team chạy offline eval và smoke test trên model cũ/mới, so sánh score, failed cases, latency/cost và contract compliance. Nếu regression vượt threshold, rollout bị chặn hoặc cần fallback.

## Project Role / Vai trò trong dự án

Dùng node này khi đổi model provider, nâng version model, tối ưu cost/latency, chuyển local model hoặc thêm routing nhiều model.

## Output / Artifact nên có

- Model/version diff
- Eval report trước/sau
- Latency/cost comparison
- Failed case list
- Fallback/rollback rule

## Decision Checklist / Câu hỏi kiểm tra

- Model mới tốt hơn ở metric nào và tệ hơn ở metric nào?
- Case critical có regress không?
- Output schema/tool call còn ổn không?
- Latency/cost có chấp nhận được không?
- Có fallback model không?

## Failure Modes / Cách nó gây lỗi

- Model mới giỏi demo nhưng kém case production.
- Format compliance giảm làm parser lỗi.
- Tool call sai nhiều hơn.
- Latency tăng làm timeout.
- Safety/grounding kém hơn nhưng không được đo.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype chưa có baseline có thể bắt đầu bằng smoke eval nhỏ.
- Không nên đổi model production chỉ vì benchmark chung nếu eval nội bộ chưa pass.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[AI Evaluation]] vì model regression cần eval định lượng/định tính.
- [[Offline Evaluation]] vì so sánh model nên chạy trên dataset cố định.
- [[Inference]] vì inference config/model version là nguồn regression.
- [[Timeout]] vì model mới có thể làm latency tăng.

## Liên quan rộng

- Model routing
- LLM reliability
- Cost latency tradeoff

## Keywords / Từ khóa tìm kiếm

- Model Regression
- model behavior regression
- model version eval
- model comparison
- LLM regression
- model fallback
- model regression debugging

## Source trace

- OpenAI documentation
- Designing Machine Learning Systems
