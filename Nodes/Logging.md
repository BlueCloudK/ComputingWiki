# Logging

Aliases: logs, ghi log

Type: Reliability / SRE

## Context / Ngữ cảnh

Logging xuất hiện khi hệ thống cần ghi lại sự kiện runtime để debug, audit, điều tra incident hoặc hiểu request/job đã đi qua những bước nào. Log thường nằm trong app, gateway, worker, database, infrastructure và security/audit path.

## Boundary / Ranh giới

### Nó là gì

Logging là việc ghi event có cấu trúc hoặc bán cấu trúc về điều gì đã xảy ra: timestamp, level, message, request id, actor, action, resource, status, latency, error context. Log tốt giúp trả lời “đã xảy ra gì” và nối được với metric/trace khi incident xảy ra.

### Nó không phải là gì

Logging không phải monitoring đầy đủ và không nên thay thế metric/alert. Log quá nhiều, thiếu cấu trúc hoặc chứa secret/PII có thể làm cost tăng và tạo risk. Logging cũng không phải nơi dump toàn bộ payload nhạy cảm chỉ để debug cho dễ.

## Core Mechanism / Cơ chế lõi

Code phát log ở các event quan trọng với level như debug/info/warn/error. Log được format, gắn correlation id/trace id, gửi tới stdout/file/collector, index và query. Structured logging giúp filter theo field thay vì grep text tự do.

## Project Role / Vai trò trong dự án

Logging giúp debug request lỗi, audit hành động nhạy cảm, reconstruct timeline incident và hiểu failure path. Khi thiết kế backend, cần quyết định log gì ở boundary, log level nào, field nào bắt buộc, dữ liệu nào phải mask và retention bao lâu.

## Output / Artifact nên có

- Logging convention: level, format, required fields, request id/trace id
- Sensitive data policy: secret/PII masking, redaction, retention
- Audit log schema cho hành động nhạy cảm
- Error log pattern: exception type, stack trace, context, user-safe message
- Query/dashboard mẫu cho incident: by request id, user id, endpoint, error code

## Decision Checklist / Câu hỏi kiểm tra

- Log này giúp debug/audit quyết định nào?
- Có request id/trace id để nối log giữa service không?
- Log level có đúng không: debug/info/warn/error?
- Có lộ password, token, secret, PII hoặc payload nhạy cảm không?
- Log có structured fields thay vì message text khó query không?
- Volume/cardinality có làm logging cost tăng quá mức không?
- Retention và access control log có phù hợp dữ liệu nhạy cảm không?

## Failure Modes / Cách nó gây lỗi

- Thiếu correlation id làm không nối được request qua gateway/backend/worker.
- Log quá ít khiến incident chỉ biết có lỗi nhưng không biết context.
- Log quá nhiều gây cost cao, noise và làm query chậm.
- Log token/secret/PII gây data leak và compliance risk.
- Log level sai làm error thật chìm trong noise hoặc info thành alert giả.
- Không log audit action nhạy cảm nên không điều tra được ai làm gì.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype nhỏ có thể dùng log đơn giản nhưng vẫn nên tránh log secret.
- Không nên thêm structured logging phức tạp nếu service chưa có nhiều request/service, nhưng nên giữ format dễ nâng cấp.
- Không nên log mọi payload chỉ để né việc thiết kế observability đúng.

## Gồm những gì

- [[Monitoring]]
- [[Incident]]

## Nối mạnh

- [[Monitoring]] vì log là một telemetry source trong monitoring/observability.
- [[Incident]] vì log giúp reconstruct timeline và root/contributing factors.
- [[Alert]] vì một số alert dựa trên log-derived metrics.
- security logging vì hành động nhạy cảm cần log audit khác log debug thường.
- Tracing vì trace id/correlation id nối log với request path phân tán.

## Liên quan rộng

- Observability
- Audit trail
- Debugging
- Compliance

## Keywords / Từ khóa tìm kiếm

- Logging
- logs
- ghi log
- structured logging
- log level
- request id
- trace id
- correlation id
- audit log
- error log
- log redaction
- PII masking
- log retention
- logging cost
- logging debugging

## Source trace

- Google SRE Book
- SWEBOK Operations
