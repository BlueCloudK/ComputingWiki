# Cloud and Infrastructure

Aliases: cloud infrastructure, hạ tầng cloud

Type: Deployment / Operations

## Context / Ngữ cảnh

Cloud and Infrastructure xuất hiện khi phần mềm cần chạy trên tài nguyên thật: compute, network, storage, identity, deployment environment và cấu hình vận hành.

## Boundary / Ranh giới

### Nó là gì

Cloud and Infrastructure là vùng kiến thức về cách provision, cấu hình và vận hành môi trường chạy hệ thống.

### Nó không phải là gì

Nó không phải chỉ là tài khoản cloud, không phải mua server rồi bỏ đó, và không thay thế architecture hay deployment process.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là biến infrastructure thành resource có owner, config, access boundary và lifecycle rõ. Hạ tầng tốt có thể tái tạo, quan sát, rollback và kiểm soát quyền.

## Project Role / Vai trò trong dự án

Vùng này giúp tránh lỗi môi trường: dev chạy được nhưng production thiếu resource, quyền, network hoặc config. Nó nối code với nơi code thật sự sống.

## Output / Artifact nên có

- Infrastructure diagram hoặc environment inventory
- IaC/config cho resource quan trọng
- Access, network và deployment notes

## Decision Checklist / Câu hỏi kiểm tra

- Resource nào cần provision và ai sở hữu?
- Environment có tái tạo được không?
- Secret, identity và network boundary đã rõ chưa?
- Monitoring/cost/backup có được tính từ đầu không?
- Change hạ tầng có review và rollback không?

## Failure Modes / Cách nó gây lỗi

- Drift giữa dev/staging/production
- Quyền cloud quá rộng gây rủi ro security
- Resource tạo tay nên không truy được lịch sử thay đổi
- Thiếu observability/cost guardrail làm vận hành mù

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần cloud architecture nặng cho app local hoặc prototype chưa deploy
- Dễ over-engineer nếu tạo platform phức tạp trước khi có nhu cầu vận hành thật

## Gồm những gì

- [[Cloud Computing]]
- [[Infrastructure as Code]]
- [[Region]]
- [[Availability Zone]]
- [[Load Balancer]]
- [[Object Storage]]
- [[VPC]]
- [[IAM]]
- [[Kubernetes]]
- [[Docker]]
- [[Terraform]]

## Nối mạnh

- [[Deployment]] vì deployment cần môi trường và resource cụ thể để chạy
- [[Monitoring]] vì hạ tầng production cần quan sát health, cost và saturation
- [[Secret]] vì cloud/infrastructure thường xử lý credential và key nhạy cảm

## Liên quan rộng

- Platform engineering
- Networking
- Cost management
- Security operations

## Source trace

- AWS Well-Architected Framework
- Google Cloud Architecture Framework
- Azure Architecture Center
