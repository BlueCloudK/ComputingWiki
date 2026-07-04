# Resource Exhaustion

Aliases: resource depletion, cạn tài nguyên

Type: Failure Pattern

## Context / Ngữ cảnh

Resource Exhaustion xuất hiện khi CPU, memory, disk, connection, file descriptor, thread, queue capacity, GPU, API quota hoặc rate limit bị dùng tới mức hệ thống không còn phục vụ request/job bình thường. Nó có thể do traffic thật, bug, leak, attack hoặc capacity planning sai.

## Boundary / Ranh giới

### Nó là gì

Resource Exhaustion là failure pattern trong đó một tài nguyên hữu hạn bị bão hòa hoặc cạn kiệt. Khi tài nguyên đó hết, request mới bị chậm, timeout, fail, queue phình ra hoặc service bị kill/restart. Đây là một dạng saturation có thể lan sang dependency khác.

### Nó không phải là gì

Resource Exhaustion không phải mọi lỗi performance. Một endpoint chậm do thuật toán kém hoặc query thiếu index có thể gây exhaustion, nhưng bản thân exhaustion tập trung vào tài nguyên nào đang bị chạm giới hạn. Cũng không nên chỉ nhìn CPU/RAM; connection, fd, quota và queue thường là nguyên nhân ẩn.

## Core Mechanism / Cơ chế lõi

Hệ thống có capacity hữu hạn. Khi demand vượt capacity hoặc resource không được release, queue/wait time tăng. Nếu không có admission control, backpressure, timeout, rate limit hoặc graceful degradation, tài nguyên bị cạn và lỗi lan rộng: thread chờ connection, retry tăng tải, log đầy disk, OOM kill hoặc quota provider bị khóa.

## Project Role / Vai trò trong dự án

Resource Exhaustion là node cần mở khi production có latency spike, OOM, disk full, too many open files, connection pool exhausted, queue backlog, GPU memory full hoặc quota exceeded. Nó giúp team xác định resource giới hạn, consumer nào dùng nhiều nhất, limit ở đâu và cơ chế bảo vệ nào thiếu.

## Output / Artifact nên có

- Resource inventory: CPU, memory, disk, fd, thread, connection, queue, quota, GPU
- Saturation dashboard: usage, limit, queue/wait time, error rate, throttle count
- Load/soak test để xác định capacity và failure mode
- Protection policy: rate limit, backpressure, timeout, circuit breaker, quota guard
- Runbook cho OOM, disk full, fd exhaustion, pool exhaustion và quota exceeded

## Decision Checklist / Câu hỏi kiểm tra

- Tài nguyên nào đang chạm limit trước: CPU, memory, disk, connection, fd, queue hay quota?
- Usage tăng do traffic hợp lệ, leak, retry storm, batch job hay attacker?
- Có metric về saturation/wait time hay chỉ có usage phần trăm?
- Khi tài nguyên gần cạn, hệ thống degrade gracefully hay fail dây chuyền?
- Có admission control/rate limit/backpressure trước dependency đắt không?
- Limit container/OS/provider có khớp workload thật không?
- Runbook có nêu cách giảm tải, scale, cleanup hoặc rollback không?

## Failure Modes / Cách nó gây lỗi

- Memory tăng tới OOM và container/process bị kill.
- Disk/log đầy làm database/app không ghi được và crash.
- File descriptor cạn làm app không mở socket/file mới được.
- Connection pool cạn làm request chờ rồi timeout hàng loạt.
- Queue backlog tăng làm job xử lý trễ và memory/disk tăng tiếp.
- API quota hết làm integration fail dù app nội bộ vẫn khỏe.
- Retry khi dependency bão hòa làm resource exhaustion nặng hơn.

## Khi nào chưa cần hoặc dễ over-engineer

- Prototype nhỏ có thể bắt đầu với monitoring cơ bản thay vì capacity model phức tạp.
- Không nên scale blindly nếu nguyên nhân thật là leak, unbounded queue hoặc retry storm.
- Không nên chỉ tăng limit mà không thêm guardrail nếu workload có thể tăng vô hạn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Memory Leak]] vì leak kéo dài thường dẫn tới resource exhaustion.
- [[Connection Pool Saturation]] vì connection pool cạn là một dạng resource exhaustion.
- [[Backpressure]] vì backpressure giúp ngăn workload vượt capacity.
- [[Rate Limiting]] vì rate limit bảo vệ tài nguyên trước traffic/abuse.
- [[Queue Backlog]] vì queue phình ra là tín hiệu tài nguyên xử lý bị bão hòa.

## Liên quan rộng

- Production reliability
- Capacity planning
- Denial of Service
- Incident response

## Keywords / Từ khóa tìm kiếm

- Resource Exhaustion
- resource depletion
- cạn tài nguyên
- resource saturation
- CPU exhaustion
- memory exhaustion
- disk full
- too many open files
- file descriptor exhaustion
- connection exhaustion
- queue backlog
- quota exceeded
- OOMKilled
- capacity limit
- resource exhaustion debugging

## Source trace

- Google SRE Book
- Linux resource limits documentation
