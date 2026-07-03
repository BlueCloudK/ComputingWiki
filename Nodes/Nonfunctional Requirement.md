# Nonfunctional Requirement

Aliases: quality requirement, yêu cầu phi chức năng

Type: Requirement / Planning

## Context / Ngữ cảnh

Nonfunctional Requirement xuất hiện khi hệ thống không chỉ cần "làm được chức năng", mà còn phải đạt mức chất lượng cụ thể như nhanh, ổn định, bảo mật, dễ vận hành hoặc chịu tải tốt.

## Boundary / Ranh giới

### Nó là gì

Nonfunctional Requirement là yêu cầu về quality attribute của hệ thống: latency, throughput, availability, reliability, security, maintainability, scalability, usability hoặc cost.

### Nó không phải là gì

Nó không phải là chức năng người dùng bấm vào, không phải lời khen kiểu "hệ thống phải tốt", và không phải giải pháp kỹ thuật nếu chưa có ngưỡng đo.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là biến chất lượng mong muốn thành target đo được trong bối cảnh cụ thể: dưới tải nào, trong bao lâu, với ngưỡng nào, đo ở đâu và ai chịu ảnh hưởng.

## Project Role / Vai trò trong dự án

NFR ép kiến trúc, testing và vận hành nhìn vào rủi ro chất lượng từ sớm. Nó quyết định caching, scaling, monitoring, threat model, deployment strategy và tiêu chí release.

## Output / Artifact nên có

- Quality target có số đo hoặc điều kiện rõ
- Scope đo: workload, user group, môi trường, thời điểm
- Mapping sang test, monitoring hoặc architecture decision

## Decision Checklist / Câu hỏi kiểm tra

- Attribute cần bảo vệ là latency, availability, security hay thứ khác?
- Target có số đo, điều kiện tải và môi trường đo chưa?
- Nếu không đạt target thì ảnh hưởng user/business nào?
- Requirement này cần test, monitor hay kiến trúc riêng không?
- Có trade-off với cost, complexity hoặc delivery time không?

## Failure Modes / Cách nó gây lỗi

- Nói "nhanh" hoặc "scalable" nhưng không có ngưỡng đo
- Chỉ phát hiện performance/security/reliability khi sắp release
- Tối ưu một quality attribute làm hỏng attribute khác
- NFR nằm trong đầu architect nhưng không trace sang test hoặc monitoring

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần target quá chặt cho prototype chưa có user thật
- Dễ over-engineer nếu đặt SLA cao hơn nhu cầu business và khả năng vận hành

## Gồm những gì

- [[Quality Attribute]]

## Nối mạnh

- [[Requirement]] vì NFR vẫn là requirement và cần được trace, test, ưu tiên
- [[Capacity Planning]] vì throughput, headroom và growth thường là NFR vận hành
- [[Scalability]] vì khả năng tăng tải là một quality concern phổ biến

## Liên quan rộng

- Architecture trade-off
- Observability
- Release criteria
- Cost management

## Source trace

- Software Requirements 3rd Ed Ch14
