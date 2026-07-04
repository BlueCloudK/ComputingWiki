# Inference

Aliases: model inference, suy luận mô hình

Type: AI / ML Engineering

## Context / Ngữ cảnh

Inference xuất hiện khi model đã được train/chọn xong và cần tạo prediction, classification, embedding, text output hoặc action decision cho input mới trong runtime thật. Nó là phần AI system chạm trực tiếp vào latency, cost, scale, reliability và user experience.

## Boundary / Ranh giới

### Nó là gì

Inference là quá trình đưa input qua model để tạo output. Trong production, inference không chỉ là `model(input)`, mà còn gồm preprocessing, batching, model serving, hardware/runtime, timeout, output validation, logging, monitoring và version control.

### Nó không phải là gì

Inference không phải training. Nó không cập nhật trọng số model chính trong lúc phục vụ request thông thường. Inference cũng không bảo đảm output đúng nếu input preprocessing sai, model version lệch, prompt/config đổi, hoặc output không được validate theo contract/use case.

## Core Mechanism / Cơ chế lõi

Pipeline inference thường gồm nhận request, validate/preprocess input, chọn model/version, chạy model trên runtime phù hợp, postprocess output, validate/guardrail, trả response và ghi log/metric. Với LLM, inference còn phụ thuộc context length, decoding config, tool call, streaming, rate limit và token cost.

## Project Role / Vai trò trong dự án

Inference ảnh hưởng tới cách AI feature được deploy và vận hành. Khi debug AI app, team phải biết model version nào đang chạy, input được preprocess ra sao, latency nằm ở model hay network, output được validate thế nào, và fallback/rollback xảy ra ra sao khi inference fail.

## Output / Artifact nên có

- Inference serving design: endpoint, model version, runtime/hardware, batching, timeout
- Input preprocessing và output postprocessing/validation contract
- Metric dashboard: latency p50/p95/p99, throughput, error rate, token/cost, saturation
- Rollout/rollback plan cho model version hoặc prompt/config version
- Test case cho malformed input, slow inference, bad output, model unavailable và fallback

## Decision Checklist / Câu hỏi kiểm tra

- Inference đang phục vụ online request, batch job hay background pipeline?
- Latency/cost budget cho request là bao nhiêu?
- Model version/prompt/config có được pin và log lại không?
- Có batching/cache/streaming phù hợp workload không?
- Output có cần schema validation, safety filter hoặc human review không?
- Khi model/provider unavailable, fallback/rollback là gì?
- Metric có tách model latency, queue time, network latency và postprocessing không?

## Failure Modes / Cách nó gây lỗi

- Model version đổi nhưng không log/version output làm regression khó trace.
- Preprocessing train/inference lệch làm output sai dù model tốt.
- Inference latency p95/p99 cao làm API timeout hoặc user experience tệ.
- Batching quá lớn làm throughput tăng nhưng latency interactive request vượt budget.
- Output không validate làm JSON sai/schema sai/action sai đi sâu vào hệ thống.
- Provider/model outage không có fallback làm toàn bộ AI feature fail.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype offline có thể gọi model đơn giản trước khi xây serving platform.
- Không nên tối ưu GPU/batching phức tạp khi bottleneck thật là prompt/context hoặc network/provider.
- Không nên deploy model mới nếu chưa có eval/regression check và rollback path rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Model Serving]] vì inference production cần lớp serving ổn định.
- [[AI Evaluation]] vì đổi inference model/config cần eval để bắt regression.
- [[Latency]] vì inference thường là phần tốn thời gian nhất trong AI request.
- [[Timeout]] vì inference chậm cần timeout/fallback rõ.
- [[Model Versioning]] vì cần biết output đến từ model/prompt/config version nào.

## Liên quan rộng

- ML operations
- AI product reliability
- Runtime optimization
- Cost control

## Keywords / Từ khóa tìm kiếm

- Inference
- model inference
- suy luận mô hình
- model serving
- online inference
- batch inference
- inference latency
- inference throughput
- model version
- inference endpoint
- batching
- output validation
- LLM inference
- token cost
- inference debugging

## Source trace

- TensorFlow Serving documentation
- PyTorch documentation
- ML systems references
