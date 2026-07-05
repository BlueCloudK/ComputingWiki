# Deployment Gate

Aliases: Deployment Gate, release gate

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Deployment Gate xuất hiện khi pipeline cần chặn hoặc cho phép deploy dựa trên test, approval, policy, metric hoặc trạng thái environment.

## Boundary / Ranh giới

### Nó là gì

Deployment Gate là checkpoint trong CD pipeline/rollout flow, nơi release phải đạt điều kiện nhất định trước khi đi tiếp.

### Nó không phải là gì

Deployment Gate không phải đảm bảo production an toàn tuyệt đối. Gate chỉ tốt nếu input signal đáng tin và không bị bypass.

## Core Mechanism / Cơ chế lõi

Pipeline hoặc rollout controller chạy test/policy/approval/metric check. Nếu gate pass, deploy tiếp; nếu fail, pipeline dừng, rollback hoặc yêu cầu người phụ trách xử lý.

## Project Role / Vai trò trong dự án

Dùng node này khi thiết kế production approval, policy check, canary gate, promotion giữa environment hoặc debug vì sao deploy bị block.

## Output / Artifact nên có

- Gate condition list
- Required checks/tests
- Approval owner nếu cần
- Failure/rollback behavior
- Audit log/run link

## Decision Checklist / Câu hỏi kiểm tra

- Gate đang bảo vệ rủi ro gì?
- Signal nào được dùng để pass/fail?
- Gate có thể bị bypass không?
- Ai approve nếu manual?
- Khi gate fail thì rollback, pause hay retry?

## Failure Modes / Cách nó gây lỗi

- Gate quá yếu nên lỗi vẫn vào production.
- Gate quá chặt làm release kẹt không cần thiết.
- Manual approval không có context metric/test.
- Gate bị bypass qua workflow thủ công.
- Failure không có owner nên deploy treo.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ chưa có production user có thể dùng test đơn giản trước.
- Không nên thêm nhiều gate nếu mỗi gate không có signal/action rõ.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Deployment Approval]] vì approval là một dạng deployment gate.
- [[CD]] vì gate nằm trong delivery pipeline.
- [[Canary Analysis]] vì canary metric có thể là rollout gate.
- [[Policy Check]] vì policy check có thể chặn deploy không đạt chuẩn.

## Liên quan rộng

- Release gate
- Production approval
- Policy enforcement

## Keywords / Từ khóa tìm kiếm

- Deployment Gate
- release gate
- CD gate
- production gate
- approval gate
- policy gate
- deployment gate debugging

## Source trace

- Continuous Delivery
- GitHub Actions documentation
- Google SRE Books
