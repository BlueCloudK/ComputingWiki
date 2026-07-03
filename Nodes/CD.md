# CD

Aliases: Continuous Delivery, Continuous Deployment, triển khai liên tục

Type: Deployment / Operations

## Context / Ngữ cảnh

CD xuất hiện khi code đã qua CI cần được đưa tới environment một cách lặp lại, kiểm soát được và ít thao tác tay.

## Boundary / Ranh giới

### Nó là gì

CD là practice tự động hóa release/deployment pipeline để build artifact có thể được đưa tới staging/production an toàn.

### Nó không phải là gì

Nó không phải chỉ copy file lên server, không thay thế rollback/monitoring, và không nhất thiết nghĩa là auto-deploy mọi commit lên production.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là promotion pipeline: build artifact, deploy vào environment, run verification, expose traffic và rollback/degrade khi signal xấu.

## Project Role / Vai trò trong dự án

CD giảm release fear và làm deployment thành routine. Nó giúp team release nhỏ hơn, quan sát tốt hơn và quay lại nhanh khi có lỗi.

## Output / Artifact nên có

- Deployment pipeline
- Release artifact và environment promotion rule
- Smoke test, rollback và approval policy nếu cần

## Decision Checklist / Câu hỏi kiểm tra

- Artifact nào được deploy và có immutable không?
- Environment nào cần promotion?
- Verification sau deploy là gì?
- Rollback hoặc roll-forward plan là gì?
- Có cần manual approval cho production không?

## Failure Modes / Cách nó gây lỗi

- Deploy tự động nhưng không verify health/user impact
- Artifact không reproducible làm rollback khó
- Pipeline thiếu approval cho change rủi ro cao
- Deploy thành công nhưng migration/config làm runtime lỗi

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần CD phức tạp nếu release rất hiếm và deploy thủ công vẫn an toàn
- Dễ over-engineer nếu tạo nhiều gate/stage làm release chậm mà không giảm rủi ro

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[CI]] vì CD dựa vào confidence và artifact từ CI
- [[Deployment]] vì CD tự động hóa deployment process
- [[Rollback]] vì pipeline production cần đường quay lại rõ
- [[Monitoring]] vì deploy decision cần signal sau release

## Liên quan rộng

- Release automation
- Progressive delivery
- Environment promotion

## Source trace

- Continuous Delivery
- Google SRE Books
