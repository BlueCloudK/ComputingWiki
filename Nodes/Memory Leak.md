# Memory Leak

Aliases: leak bộ nhớ, rò rỉ bộ nhớ

Type: Failure Pattern

## Context / Ngữ cảnh

Memory Leak xuất hiện khi process chạy lâu và bộ nhớ tăng dần vì object, buffer, listener, cache entry, goroutine/thread hoặc reference vẫn bị giữ sau khi không còn cần. Nó thường gặp ở web server, worker, browser app, stream processor, game loop hoặc service xử lý nhiều request theo thời gian.

## Boundary / Ranh giới

### Nó là gì

Memory Leak là failure pattern trong đó memory không được giải phóng hoặc không thể được garbage collector thu hồi vì vẫn còn reference sống. Với ngôn ngữ có GC, leak thường là giữ reference quá lâu; với ngôn ngữ quản lý bộ nhớ thủ công, leak có thể là cấp phát nhưng không free.

### Nó không phải là gì

Memory Leak không phải mọi tình huống dùng nhiều RAM. Cache có giới hạn, warm-up memory, batch job cần buffer lớn hoặc model AI load vào RAM có thể là memory footprint hợp lệ. Leak thường có dấu hiệu tăng theo thời gian/tải và không giảm về baseline sau khi workload kết thúc.

## Core Mechanism / Cơ chế lõi

Leak xảy ra khi object graph vẫn reachable dù logic không còn cần nó, ví dụ unbounded cache, event listener không remove, closure giữ object lớn, collection static/global, response buffer không giải phóng, goroutine/thread không dừng hoặc native resource không close. Hậu quả là heap growth, GC pressure, latency tăng và cuối cùng OOM/restart.

## Project Role / Vai trò trong dự án

Memory Leak là node cần mở khi service sau vài giờ/ngày mới chậm, container bị OOMKilled, browser tab nặng dần hoặc worker cần restart định kỳ. Nó giúp team chuyển từ “RAM cao” sang kiểm tra heap profile, allocation path, object retention, cache limit, lifecycle cleanup và memory metric.

## Output / Artifact nên có

- Memory dashboard: RSS/heap, GC time, allocation rate, OOM/restart count
- Heap dump/profile hoặc memory timeline trước/sau workload
- Leak reproduction scenario: request loop, long-running job hoặc browser interaction
- Ownership/lifecycle note cho cache, listener, stream, worker, file/socket handle
- Fix verification bằng soak test hoặc load test kéo dài

## Decision Checklist / Câu hỏi kiểm tra

- Memory có tăng liên tục theo thời gian hay chỉ tăng tới plateau?
- Sau khi workload dừng, memory có quay gần baseline không?
- Có unbounded cache/list/map/queue nào không?
- Listener/subscription/timer/stream có được cleanup khi object/session kết thúc không?
- Heap profile chỉ ra object type nào giữ nhiều memory nhất?
- Container memory limit có quá thấp so với workload hợp lệ không?
- OOM xảy ra do heap, native memory, buffer, thread stack hay external process?

## Failure Modes / Cách nó gây lỗi

- Unbounded cache giữ dữ liệu user/request mãi và làm heap tăng dần.
- Event listener hoặc subscription không remove làm object cũ vẫn reachable.
- Goroutine/thread/timer leak giữ resource dù request đã kết thúc.
- Buffer/file/socket không close làm native memory hoặc file descriptor tăng.
- GC chạy thường xuyên hơn làm latency tăng trước khi OOM.
- Container bị OOMKilled, service restart lặp lại và mất request/job đang xử lý.

## Khi nào chưa cần hoặc dễ over-engineer

- RAM cao nhưng ổn định sau warm-up không nhất thiết là leak.
- Không nên tối ưu memory bằng cảm giác trước khi có profile/metric.
- Batch job ngắn có thể dùng memory lớn nếu trong giới hạn rõ và không ảnh hưởng service dài hạn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Resource Exhaustion]] vì leak kéo dài thường dẫn tới cạn tài nguyên.
- [[Monitoring]] vì cần metric để phân biệt leak với usage hợp lệ.
- [[Load Test]] vì leak thường lộ sau workload dài hoặc concurrency cao.
- [[Garbage Collection]] vì GC pressure là dấu hiệu quan trọng trong runtime có GC.

## Liên quan rộng

- Runtime debugging
- Performance profiling
- Container operations
- Browser performance

## Keywords / Từ khóa tìm kiếm

- Memory Leak
- leak bộ nhớ
- rò rỉ bộ nhớ
- heap growth
- memory profiling
- heap dump
- object retention
- unbounded cache
- listener leak
- goroutine leak
- thread leak
- OOM
- OOMKilled
- GC pressure
- memory leak debugging

## Source trace

- Java memory management documentation
- Chrome memory profiling documentation
