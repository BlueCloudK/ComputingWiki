# Environment Variable

Aliases: env var, biến môi trường

Type: Deployment / Operations

## Context / Ngữ cảnh

Environment Variable xuất hiện khi code cần chạy ổn định trong staging/production với environment, config, health check, log và rollback rõ ràng.

## Boundary / Ranh giới

### Nó là gì

Environment Variable là phần biến code thành service vận hành được và troubleshoot được.

### Nó không phải là gì

Nó không chỉ là lệnh deploy; nếu thiếu monitoring, rollback và config discipline thì release vẫn rủi ro cao.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là kiểm soát môi trường chạy: config, dependency, health signal, log/metric, release step và rollback path.

## Project Role / Vai trò trong dự án

Environment Variable ảnh hưởng tới release safety, incident response, troubleshooting và khả năng phục hồi khi deploy lỗi.

## Output / Artifact nên có

- Deployment/runbook hoặc config checklist theo environment
- Health check, logging và monitoring signal tối thiểu
- Rollback plan và troubleshooting note cho lỗi thường gặp

## Decision Checklist / Câu hỏi kiểm tra

- Environment/config khác nhau đã được ghi rõ chưa?
- Health check có phản ánh service thật sự usable không?
- Log có đủ context để debug nhưng không lộ secret không?
- Rollback có được thử hoặc ít nhất mô tả rõ không?
- Incident path có owner và bước troubleshooting không?

## Failure Modes / Cách nó gây lỗi

- Config lệch giữa môi trường gây lỗi chỉ xuất hiện ở production
- Health check xanh nhưng chức năng chính hỏng
- Không có rollback nên release lỗi kéo dài
- Log thiếu context hoặc quá ồn làm incident khó xử lý

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần pipeline/runbook phức tạp cho app thử nghiệm chưa deploy
- Dễ over-engineer nếu tạo quá nhiều môi trường/tool khi team chưa vận hành nổi

## Gồm những gì

- [[Secret]]
- [[Deployment]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- DevOps
- Production operations
- Release management
- Troubleshooting

## Source trace

- Deployment and Operations
