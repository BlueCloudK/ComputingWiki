# AI Application Engineering Path

## Mục tiêu

Path này giúp người đọc đi từ dữ liệu, model, inference tới RAG, evaluation và vận hành AI application.

## Khi nào dùng path này

- Khi xây app dùng LLM, embedding hoặc ML model.
- Khi cần hiểu data/eval/inference thay vì chỉ prompt.
- Khi muốn đưa AI feature vào production có kiểm soát.

## 1. Nền ML/AI

- [[Machine Learning]] — nền về hệ thống học từ dữ liệu.
- [[Dataset]] — dữ liệu dùng để train/evaluate.
- [[Training Data]] — dữ liệu model học từ đó.
- [[Model Training]] — quá trình train model.
- [[Inference]] — dùng model để tạo prediction/output.
- [[Model Serving]] — đưa model vào service phục vụ request.

## 2. Data và quality

- [[Data Pipeline]] — luồng tạo/chuyển dữ liệu.
- [[Data Quality]] — dữ liệu đủ đúng, đủ sạch và đủ tin để dùng.
- [[Data Leakage]] — lỗi làm eval quá đẹp nhưng production fail.
- [[Train Test Split]] — chia dữ liệu để đánh giá đúng.
- [[Validation Set]] — chọn model/config.
- [[Test Set]] — đánh giá cuối cùng.

## 3. Evaluation

- [[AI Evaluation]] — đánh giá output/hành vi của AI system.
- [[Evaluation Metric]] — metric đo model hoặc feature.
- [[Precision]] — đo positive prediction đúng.
- [[Recall]] — đo positive thật được tìm ra.
- [[F1 Score]] — cân bằng precision và recall.
- [[Experiment Tracking]] — ghi lại config/dataset/metric/artifact.

## 4. LLM application

- [[LLM]] — model ngôn ngữ lớn sinh/hiểu text.
- [[Token]] — đơn vị text model xử lý.
- [[Context Window]] — giới hạn context model thấy.
- [[Prompt Engineering]] — thiết kế prompt để điều khiển output.
- [[Prompt Injection]] — attack làm model/tool làm sai ý định.
- [[Fine Tuning]] — điều chỉnh model bằng data riêng.

## 5. RAG và retrieval

- [[Embedding]] — vector biểu diễn meaning của text/object.
- [[Vector Database]] — lưu và query embedding.
- [[Vector Index]] — tìm vector gần nhau nhanh.
- [[Similarity Search]] — tìm nội dung tương tự.
- [[Retrieval]] — lấy context liên quan.
- [[RAG]] — kết hợp retrieval với generation.

## 6. Production AI

- [[MLOps]] — lifecycle vận hành model/data/eval.
- [[Model Registry]] — quản lý version model artifact.
- [[Model Drift]] — model kém dần do data/world thay đổi.
- [[Inference Latency]] — độ trễ khi model trả output.
- [[Online Inference]] — inference realtime.
- [[Batch Inference]] — inference theo lô.

## Missing / Future nodes

Các khái niệm nên bổ sung sau, ghi text thường, không wikilink:

- Agent
- Tool calling
- Guardrail
- Eval dataset
- Hallucination
- Retrieval quality
- Vector chunking

## Related paths

- [[Backend Engineering Path]]
- [[Database Engineering Path]]
- [[Security Engineering Path]]
- [[Debugging and Failure Patterns Path]]
