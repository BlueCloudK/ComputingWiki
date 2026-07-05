# Tool Retry

Aliases: Tool Retry, tool call retry

Type: AI / RAG / Agent Engineering

## Context / Ngữ cảnh

Tool Retry xuất hiện khi AI agent/tool runner gọi API, database, browser, file system hoặc external service và tool call có thể fail tạm thời.

## Boundary / Ranh giới

### Nó là gì

Tool Retry là policy chạy lại tool call sau lỗi có thể phục hồi, thường với giới hạn số lần, backoff và điều kiện retry rõ.

### Nó không phải là gì

Tool Retry không phải cách sửa mọi lỗi tool. Lỗi permission, schema sai, validation fail hoặc action không idempotent thường không nên retry mù.

## Core Mechanism / Cơ chế lõi

Tool runner phân loại lỗi, quyết định có retry không, chờ theo backoff/jitter, chạy lại với cùng hoặc argument đã chỉnh, rồi ghi trace cho mỗi attempt.

## Project Role / Vai trò trong dự án

Dùng node này khi debug agent loop bị lặp, API flake, rate limit, timeout, tool side effect bị chạy nhiều lần hoặc cost tăng do retry sai.

## Output / Artifact nên có

- Retryable error list
- Max attempt / timeout budget
- Backoff and jitter rule
- Idempotency requirement
- Attempt trace/log

## Decision Checklist / Câu hỏi kiểm tra

- Lỗi này có tạm thời không?
- Tool call có idempotent không?
- Retry có làm side effect lặp không?
- Tổng timeout/cost budget là bao nhiêu?
- Khi retry hết thì fallback/escalate thế nào?

## Failure Modes / Cách nó gây lỗi

- Retry action ghi/xóa làm side effect lặp.
- Retry rate limit làm bị throttle nặng hơn.
- Retry che lỗi schema/permission thật.
- Agent loop vừa retry tool vừa tự retry plan làm nổ số attempt.
- Không log attempt nên không biết lỗi xảy ra ở lần nào.

## Khi nào chưa cần hoặc dễ over-engineer

- Tool local deterministic có thể fail-fast trước.
- Không nên retry tool write action nếu chưa có idempotency key hoặc compensation path.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Tool Use]] vì retry là behavior của tool runner.
- [[Tool Error]] vì retry phụ thuộc phân loại lỗi tool.
- [[Timeout]] vì retry phải nằm trong timeout budget.
- [[Retry]] vì đây là pattern retry áp cho agent tool call.

## Liên quan rộng

- Backoff
- Idempotency
- Agent trace

## Keywords / Từ khóa tìm kiếm

- Tool Retry
- tool call retry
- agent tool retry
- retry backoff
- idempotent tool
- retry budget
- tool retry debugging

## Source trace

- OpenAI documentation
- Google SRE Books
