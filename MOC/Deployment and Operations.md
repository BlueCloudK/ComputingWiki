# Deployment and Operations

Aliases: operations, SRE, production, deploy và vận hành

Type: Deployment / Operations

## Bản chất

Deployment and Operations là vùng biến code thành service chạy được, quan sát được và phục hồi được trong môi trường thật. Nó bao gồm environment, config, health check, logging, monitoring, rollback và troubleshooting.

## Dùng trong dự án để làm gì

Deployment and Operations là MOC để tìm các node phục vụ release, cấu hình môi trường, vận hành và xử lý sự cố. Khi chuẩn bị đưa hệ thống lên staging/production, dùng trang này để kiểm tra thứ gì cần có trước khi deploy.

## Khi nào cần quan tâm

- Chuẩn bị deploy staging/production hoặc đổi config
- Service cần health check, log và dashboard để vận hành
- Release có rủi ro cần rollback
- Incident cần troubleshooting theo environment cụ thể

## Output / artifact nên có

- Deployment/runbook hoặc config checklist theo environment
- Health check, logging và monitoring signal tối thiểu
- Rollback plan và troubleshooting note cho lỗi thường gặp

## Checklist kiểm tra

- Environment/config khác nhau đã được ghi rõ chưa?
- Health check có phản ánh service thật sự usable không?
- Log có đủ context để debug nhưng không lộ secret không?
- Rollback có được thử hoặc ít nhất mô tả rõ không?
- Incident path có owner và bước troubleshooting không?

## Lỗi / rủi ro thường gặp

- Config lệch giữa môi trường gây lỗi chỉ xuất hiện ở production
- Health check xanh nhưng chức năng chính hỏng
- Không có rollback nên release lỗi kéo dài
- Log thiếu context hoặc quá ồn làm incident khó xử lý

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần pipeline/runbook phức tạp cho app thử nghiệm chưa deploy
- Dễ over-engineer nếu tạo quá nhiều môi trường/tool khi team chưa vận hành nổi

## Gồm những gì

- [[Deployment]]
- [[Environment Variable]]
- [[Logging]]
- [[Monitoring]]
- [[Incident]]
- [[Rollback]]
- [[Backup]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- SWEBOK Map
- SRE Map
