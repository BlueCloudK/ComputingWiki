# Rollback

Aliases: revert deployment, quay lại phiên bản trước

Type: Reliability / SRE

## Context / Ngữ cảnh

Rollback xuất hiện khi version mới, config mới, migration mới hoặc rollout mới gây lỗi và team cần quay lại trạng thái an toàn hơn để giảm user impact. Nó là một mitigation quan trọng trong incident response và deployment strategy.

## Boundary / Ranh giới

### Nó là gì

Rollback là hành động đưa hệ thống về version/config/state trước đó hoặc một trạng thái đã biết là ổn. Rollback có thể là revert app version, đổi traffic về blue environment, rollback Helm release, revert feature flag, restore config hoặc khôi phục dữ liệu từ backup nếu cần.

### Nó không phải là gì

Rollback không phải luôn đơn giản hoặc luôn khả thi. Nếu database migration không backward compatible, data đã bị mutate, external side effect đã xảy ra hoặc version cũ không còn tương thích config mới, rollback app code có thể không đủ. Rollback cũng không thay thế fix lâu dài; nó giảm impact trước.

## Core Mechanism / Cơ chế lõi

Khi metric/alert/user report cho thấy release lỗi, team xác định change gần nhất và rollback path an toàn nhất. Hệ thống chuyển traffic/version/config về trạng thái trước, verify recovery bằng monitoring, rồi giữ timeline để postmortem. Rollback tốt cần artifact versioned, migration plan và command được test trước.

## Project Role / Vai trò trong dự án

Rollback là node cần mở khi thiết kế deploy, migration, feature flag hoặc incident response. Nó buộc team hỏi trước khi release: nếu lỗi thì quay lại bằng cách nào, mất bao lâu, rollback có phá dữ liệu không, và ai có quyền chạy rollback.

## Output / Artifact nên có

- Rollback plan: trigger, owner, command, expected duration, validation metric
- Versioned artifact/config để quay lại đúng trạng thái
- Migration rollback/forward-fix note nếu database/data đổi
- Traffic rollback path nếu dùng blue-green/canary/load balancer
- Post-rollback verification checklist: error rate, latency, health, data correctness

## Decision Checklist / Câu hỏi kiểm tra

- Rollback trigger là gì: error rate, latency, SLO burn, user report hay manual decision?
- Artifact/config version cũ còn sẵn không?
- Database migration có backward compatible với app version cũ không?
- Rollback có làm mất dữ liệu hoặc duplicate side effect không?
- Ai có quyền rollback và command đã được thử chưa?
- Sau rollback, metric nào chứng minh impact đã giảm?
- Nếu rollback không khả thi, forward fix hoặc mitigation thay thế là gì?

## Failure Modes / Cách nó gây lỗi

- App rollback nhưng database schema đã đổi không tương thích.
- Config/secret mới vẫn còn nên version cũ cũng lỗi.
- Rollback không drain traffic làm request đang xử lý bị cắt.
- Không biết exact version trước đó nên rollback nhầm.
- External side effect như email/payment đã xảy ra nên rollback code không đảo ngược business impact.
- Không verify sau rollback nên tưởng đã ổn nhưng user flow chính vẫn lỗi.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype local có thể dùng git revert/redeploy đơn giản.
- Không nên xây rollback phức tạp nếu release nhỏ và forward fix nhanh hơn, nhưng phải biết trade-off.
- Không nên deploy change không rollback được mà không có mitigation/backup/approval rõ.

## Gồm những gì

- [[Deployment]]
- [[Backup]]

## Nối mạnh

- [[Deployment Strategy]] vì strategy tốt phải định nghĩa rollback path.
- [[Incident Response]] vì rollback là mitigation phổ biến khi incident do release gây ra.
- [[Database Migration]] vì migration quyết định rollback có an toàn không.
- [[Load Balancer]] vì traffic rollback thường đi qua LB/target group.
- [[Monitoring]] vì rollback cần metric để trigger và verify recovery.

## Liên quan rộng

- Release safety
- Change management
- Disaster recovery
- Forward fix

## Keywords / Từ khóa tìm kiếm

- Rollback
- revert deployment
- quay lại phiên bản trước
- rollback plan
- deployment rollback
- config rollback
- database rollback
- Helm rollback
- traffic rollback
- blue green rollback
- rollback trigger
- rollback verification
- forward fix
- rollback debugging

## Source trace

- Continuous Delivery
- Google SRE Books
