# Rate Limiting

Aliases: request throttling, giới hạn tốc độ request

Type: API / Integration

## Context / Ngữ cảnh

Rate Limiting xuất hiện khi API hoặc service cần giới hạn tốc độ request để bảo vệ capacity, cost, fairness hoặc abuse boundary.

## Boundary / Ranh giới

### Nó là gì

Rate Limiting là policy giới hạn số request/action trong một khoảng thời gian theo user, token, IP, tenant hoặc endpoint.

### Nó không phải là gì

Nó không phải authentication, không thay thế authorization, và không sửa bottleneck gốc nếu hệ thống đã quá chậm.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đếm request theo key/window rồi allow, throttle hoặc reject. API cần trả response rõ để client biết khi nào retry.

## Project Role / Vai trò trong dự án

Rate Limiting giúp API sống sót trước spike, bot, retry loop hoặc consumer lỗi. Nó cũng giúp chia tài nguyên công bằng giữa tenant/user.

## Output / Artifact nên có

- Rate limit policy theo endpoint/consumer
- Error response và retry guidance
- Monitoring cho limit hit, abuse và false positive

## Decision Checklist / Câu hỏi kiểm tra

- Limit theo IP, user, token, tenant hay endpoint?
- Window và burst size là bao nhiêu?
- Client nhận error/retry-after như thế nào?
- Limit này bảo vệ capacity, cost hay security?
- Có exception cho internal service hoặc premium plan không?

## Failure Modes / Cách nó gây lỗi

- Limit quá thấp làm client hợp lệ bị chặn
- Limit quá cao không bảo vệ được overload
- Không có retry guidance làm client retry loạn
- Key chọn sai khiến attacker né limit dễ dàng

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần rate limit phức tạp cho API nội bộ rất ít traffic
- Dễ over-engineer nếu chưa biết traffic pattern hoặc abuse risk

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[API Security]] vì rate limiting là control chống abuse phổ biến
- [[Overload Handling]] vì limit giúp bảo vệ service khi tải vượt capacity
- [[Backpressure]] vì cả hai đều điều tiết flow khi consumer/producer quá nhanh

## Liên quan rộng

- Quota
- Abuse prevention
- Fairness policy

## Keywords / Từ khóa tìm kiếm

- Rate Limiting
- request throttling
- giới hạn tốc độ request
- rate
- limiting
- API
- Integration

## Source trace

- OWASP API Security Top 10
- Google API Design Guide
