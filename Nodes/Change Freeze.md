# Change Freeze

Aliases: Change Freeze, deployment freeze

Type: Cloud / DevOps Tooling

## Context / Ngữ cảnh

Change Freeze xuất hiện khi hệ thống cần hạn chế hoặc tạm dừng thay đổi trong giai đoạn rủi ro cao như peak traffic, event lớn, incident, audit hoặc release window nhạy cảm.

## Boundary / Ranh giới

### Nó là gì

Change Freeze là policy vận hành quy định loại thay đổi nào bị dừng, loại nào được phép, ai có quyền exception và thời gian áp dụng.

### Nó không phải là gì

Change Freeze không phải ngừng mọi hoạt động kỹ thuật. Bug fix khẩn cấp, security fix hoặc rollback vẫn cần path rõ thay vì bị chặn mù.

## Core Mechanism / Cơ chế lõi

Team xác định freeze window, scope hệ thống, allowed change, approval/exception flow và communication channel. CI/CD hoặc deployment approval có thể enforce freeze bằng gate.

## Project Role / Vai trò trong dự án

Dùng node này khi chuẩn bị event lớn, production peak, holiday release, incident stabilization hoặc change management cho hệ thống quan trọng.

## Output / Artifact nên có

- Freeze window
- Scope service/environment
- Allowed/blocked change list
- Exception approval rule
- Communication and audit log

## Decision Checklist / Câu hỏi kiểm tra

- Freeze áp cho service/environment nào?
- Change nào vẫn được phép?
- Ai approve exception?
- Emergency rollback có bị chặn không?
- Team/on-call có biết policy chưa?

## Failure Modes / Cách nó gây lỗi

- Freeze quá rộng làm chậm fix cần thiết.
- Không có exception path nên team bypass không audit.
- Freeze chỉ thông báo bằng miệng, pipeline vẫn deploy tự do.
- Không phân biệt deploy code, config, data migration và rollback.
- Hết freeze nhưng không có review change backlog.

## Khi nào chưa cần hoặc dễ over-engineer

- Project nhỏ, chưa có production traffic đáng kể có thể chưa cần freeze formal.
- Không nên dùng freeze để thay thế test, rollback và progressive delivery.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Deployment Approval]] vì freeze thường được enforce bằng approval gate.
- [[CD]] vì change freeze tác động trực tiếp pipeline deploy.
- [[Incident Response]] vì freeze có thể dùng để ổn định hệ thống sau incident.
- [[Rollback]] vì rollback nên là exception được phép trong freeze.

## Liên quan rộng

- Change management
- Release governance
- Production stability

## Keywords / Từ khóa tìm kiếm

- Change Freeze
- deployment freeze
- release freeze
- freeze window
- emergency change
- production change control
- change freeze debugging

## Source trace

- Google SRE Books
- Continuous Delivery
