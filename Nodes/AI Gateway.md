# AI Gateway

Aliases: LLM gateway, model gateway, cổng AI

Type: AI / Platform Engineering

## Context / Ngữ cảnh

AI Gateway là lớp trung gian quản lý traffic từ application tới model provider, thường dùng cho routing, auth, logging, rate limit và policy.

## Boundary / Ranh giới

### Nó là gì

AI Gateway là control plane/runtime boundary cho request AI: app gọi gateway, gateway quyết định provider/model/policy trước khi gửi tiếp.

### Nó không phải là gì

Nó không tự làm model an toàn; prompt injection defense, eval và data policy vẫn cần thiết ở layer khác.

## Core Mechanism / Cơ chế lõi

Gateway nhận request, áp dụng authentication, quota, model routing, logging/redaction, retry/fallback và đôi khi chuẩn hóa API giữa nhiều provider.

## Project Role / Vai trò trong dự án

Node này giúp vận hành AI app khi cần kiểm soát cost, latency, audit, model switch và policy thay vì để từng service gọi provider trực tiếp.

## Output / Artifact nên có

- Gateway config cho provider/model routing
- Rate limit và quota policy
- Redaction/logging policy cho prompt và output

## Decision Checklist / Câu hỏi kiểm tra

- Request AI nào cần đi qua gateway thay vì gọi provider trực tiếp?
- Log có che secret/PII và vẫn đủ audit không?
- Fallback model có làm đổi output contract không?
- Gateway có trở thành single point of failure không?

## Failure Modes / Cách nó gây lỗi

- Log prompt/output chứa dữ liệu nhạy cảm
- Routing sai model làm chất lượng hoặc cost lệch mạnh
- Fallback không tương thích schema khiến downstream parse fail

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần gateway riêng cho prototype một service, một provider, traffic thấp
- Dễ over-engineer nếu thêm gateway trước khi có nhu cầu audit, routing hoặc cost control rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Model Routing]] vì gateway thường là nơi thực thi routing giữa model/provider
- [[Rate Limiting]] vì gateway thường enforce quota cho request AI

## Liên quan rộng

- AI platform
- Cost control
- Observability
- Policy enforcement

## Keywords / Từ khóa tìm kiếm

- AI Gateway
- LLM gateway
- model gateway
- model routing gateway
- AI proxy
- prompt logging
- provider routing
- cổng AI

## Source trace

- OpenAI API documentation
- Envoy gateway pattern references
- Cloudflare AI Gateway documentation
