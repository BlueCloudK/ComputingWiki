# Environment Variable

Aliases: env var, biến môi trường

Type: Deployment / Operations

## Bản chất

Environment Variable nằm ở phần đưa hệ thống chạy đúng môi trường và giữ nó quan sát được. Nó liên quan tới environment, config, release, health check, log, rollback và troubleshooting khi có lỗi thật. Nó nối với các phần liên quan như [[Secret]], [[Deployment]] và nhóm quyết định quanh environment variable.

## Dùng trong dự án để làm gì

Environment Variable giúp biến code thành service có thể deploy, monitor và phục hồi. Trong dự án, nó giảm rủi ro 'chạy máy tôi được' nhưng fail ở staging/production.

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

- [[Secret]]
- [[Deployment]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Deployment and Operations
