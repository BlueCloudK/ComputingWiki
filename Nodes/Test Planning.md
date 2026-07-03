# Test Planning

Aliases: test plan, lập kế hoạch kiểm thử

Type: Requirement / Planning

## Context / Ngữ cảnh

Test Planning xuất hiện khi team cần quyết định sẽ kiểm thử cái gì, bằng mức độ nào, theo rủi ro nào và trong giai đoạn nào của delivery.

## Boundary / Ranh giới

### Nó là gì

Test Planning là hoạt động xác định objective, scope, approach, resource, schedule, risk và deliverable của testing.

### Nó không phải là gì

Nó không phải là danh sách test case chi tiết, không phải automation script, và không phải đảm bảo chất lượng nếu không gắn với risk và coverage.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là ưu tiên testing theo mục tiêu và rủi ro: feature nào cần test, loại test nào phù hợp, môi trường nào cần chuẩn bị, ai chịu trách nhiệm và tiêu chí dừng là gì.

## Project Role / Vai trò trong dự án

Test Planning giúp testing không bị dồn vào cuối dự án. Nó nối requirement, risk, test objective và release decision thành một kế hoạch kiểm chứng có thể thực hiện.

## Output / Artifact nên có

- Test objectives và test scope
- Risk-based priority và test approach
- Environment, data, responsibility và exit criteria

## Decision Checklist / Câu hỏi kiểm tra

- Rủi ro nào cần testing bảo vệ nhất?
- Loại test nào cần cho từng risk: unit, integration, API, E2E, performance?
- Cần test data và environment nào?
- Khi nào đủ test để release hoặc stop?
- Phần nào cố ý không test trong batch này?

## Failure Modes / Cách nó gây lỗi

- Viết plan chung chung nhưng không ưu tiên theo rủi ro
- Automation nhiều nhưng không cover requirement quan trọng
- Thiếu test data hoặc environment nên plan không chạy được
- Không có exit criteria nên release decision cảm tính

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần test plan formal cho experiment nhỏ không release
- Dễ over-engineer nếu plan dài hơn khả năng thực thi của team

## Gồm những gì

- [[Test Objective]]
- [[Risk and Testing]]

## Nối mạnh

- [[Requirement]] vì testing cần biết requirement nào phải được kiểm chứng
- [[Acceptance Criteria]] vì criteria thường chuyển thành test condition
- [[Test Coverage]] vì plan cần biết coverage nào là đủ cho rủi ro hiện tại

## Liên quan rộng

- Release readiness
- QA strategy
- Test environment management

## Keywords / Từ khóa tìm kiếm

- Test Planning
- test planning checklist
- test planning strategy
- kiểm thử Planning
- test plan
- lập kế hoạch kiểm thử
- Test Objective
- Risk and Testing

## Source trace

- Software Testing ISTQB Map / Ch05
