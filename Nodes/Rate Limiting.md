# Rate Limiting

Aliases: request throttling, giới hạn tốc độ request

Type: API / Integration

## Context / Ngữ cảnh

Rate Limiting xuất hiện khi API, gateway, service hoặc expensive operation cần giới hạn tốc độ request/action để bảo vệ capacity, cost, fairness và abuse boundary. Nó thường dùng cho public API, login endpoint, AI inference, search, file upload, webhook, payment hoặc multi-tenant SaaS.

## Boundary / Ranh giới

### Nó là gì

Rate Limiting là policy giới hạn số request/action trong một khoảng thời gian theo key như IP, user, token, tenant, API key, endpoint hoặc model/provider. Khi vượt limit, hệ thống có thể reject, throttle, queue có kiểm soát hoặc trả 429 với hướng dẫn retry.

### Nó không phải là gì

Rate Limiting không phải authentication hoặc authorization. Nó không quyết định user là ai hay được làm gì, mà quyết định tốc độ dùng tài nguyên. Nó cũng không sửa bottleneck gốc nếu service đã chậm; limit chỉ bảo vệ hệ thống khỏi tải vượt capacity hoặc abuse.

## Core Mechanism / Cơ chế lõi

Hệ thống đếm request theo key và window. Algorithm có thể là fixed window, sliding window, token bucket hoặc leaky bucket. Policy cần quyết định burst size, sustained rate, scope, storage counter, distributed consistency, response code/header và exception cho plan/internal service nếu có.

## Project Role / Vai trò trong dự án

Rate Limiting là node cần mở khi API bị bot/spike/retry loop, AI cost tăng, một tenant chiếm tài nguyên, login bị brute force hoặc dependency bị quá tải. Nó giúp team thiết kế limit theo consumer, endpoint, cost và failure response thay vì chặn bừa.

## Output / Artifact nên có

- Rate limit policy: key, window, burst, sustained rate, endpoint/scope
- Error response: 429 body, `Retry-After`, rate-limit headers nếu dùng
- Metric: limit hit, allowed/rejected, key hot, false positive, bypass/exception
- Abuse/cost protection rule cho endpoint đắt
- Test case cho burst, sustained overload, distributed instance và credentialed user/IP mix

## Decision Checklist / Câu hỏi kiểm tra

- Limit theo IP, user, token, API key, tenant hay endpoint?
- Limit bảo vệ capacity, cost, fairness hay security abuse?
- Window/burst có phù hợp traffic thật và UX không?
- Client nhận 429 và retry thế nào?
- Có cần limit khác nhau theo plan/role/internal service không?
- Counter đặt ở app, gateway, Redis hay provider layer?
- Attacker có né limit bằng đổi IP/token/header được không?

## Failure Modes / Cách nó gây lỗi

- Limit quá thấp làm client hợp lệ bị chặn trong traffic bình thường.
- Limit quá cao không bảo vệ được backend/provider cost.
- Key sai, ví dụ chỉ theo IP sau NAT, làm nhiều user hợp lệ bị chung limit.
- Key quá dễ đổi làm attacker né limit.
- Không trả retry guidance làm client retry loạn và tăng tải.
- Distributed counter không đồng bộ làm mỗi instance cho phép vượt tổng limit.
- Bypass cho internal service quá rộng tạo đường abuse không bị giới hạn.

## Khi nào chưa cần hoặc dễ over-engineer

- API nội bộ traffic thấp và đã có network boundary tốt có thể dùng limit đơn giản hoặc chưa cần.
- Không nên thêm nhiều tầng rate limit khi chưa biết traffic pattern và abuse risk.
- Không nên dùng rate limit thay thế authorization hoặc quota/billing policy rõ ràng.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Backpressure]] vì rate limiting là một dạng điều tiết upstream để bảo vệ capacity.
- [[API Gateway]] vì gateway thường enforce rate limit ở biên API.
- [[Thundering Herd]] vì rate limit giúp làm phẳng spike đồng loạt.
- [[Resource Exhaustion]] vì rate limit ngăn request làm cạn tài nguyên.
- [[Authentication]] vì key limit thường dựa trên user/token/API key đã xác thực.

## Liên quan rộng

- Quota
- Abuse prevention
- Fairness policy
- Cost control

## Keywords / Từ khóa tìm kiếm

- Rate Limiting
- request throttling
- giới hạn tốc độ request
- request quota
- throttling
- burst limit
- token bucket
- leaky bucket
- sliding window
- 429 Too Many Requests
- Retry-After
- per user limit
- per tenant limit
- abuse protection
- rate limit debugging

## Source trace

- OWASP API Security Top 10
- Google API Design Guide
