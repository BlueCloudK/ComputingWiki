# Event Loop

Aliases: Event Loop, event loop, microtask, task queue

Type: Web Development

## Context / Ngữ cảnh

Event Loop xuất hiện khi JavaScript runtime cần xử lý async callback, promise, timer, network event, UI event và rendering mà không block main thread liên tục. Nó quan trọng trong browser frontend, Node.js service, worker, animation, input responsiveness và debugging async race.

## Boundary / Ranh giới

### Nó là gì

Event Loop là cơ chế runtime điều phối call stack, task queue, microtask queue và các phase/event source để code JavaScript chạy theo thứ tự cụ thể. Nó giải thích vì sao promise callback chạy trước timer, vì sao long task làm UI đơ, và vì sao async code không tự chạy song song trên main thread.

### Nó không phải là gì

Event Loop không phải multithreading đầy đủ. JavaScript có thể dùng worker/thread pool cho một số việc, nhưng code JS trên một event loop vẫn chạy từng đoạn một trên call stack. Event loop cũng không thay thế hiểu network/database latency; nó chỉ giải thích scheduling trong runtime.

## Core Mechanism / Cơ chế lõi

Synchronous code chạy trên call stack. Khi async operation hoàn thành, callback được đưa vào task hoặc microtask queue. Sau mỗi task, runtime thường drain microtask queue trước khi tiếp tục task khác hoặc render. Browser còn có render pipeline; Node.js có các phase riêng như timers, poll, check và microtasks.

## Project Role / Vai trò trong dự án

Event Loop là node cần mở khi debug UI freeze, promise order, debounce/throttle, timer không chạy đúng lúc, Node.js throughput thấp, unhandled promise, async race hoặc long CPU task. Nó giúp team phân biệt code đang block main thread hay đang chờ I/O thật.

## Output / Artifact nên có

- Async flow timeline: sync code, microtask, task, render, I/O callback
- Performance note cho long task/main thread blocking
- Test case cho promise/timer/order nếu behavior quan trọng
- Metric: long task duration, event loop lag, input delay, Node.js event loop utilization
- Refactor decision: split work, worker, queue, debounce/throttle, backpressure

## Decision Checklist / Câu hỏi kiểm tra

- Code này chạy đồng bộ lâu trên main thread không?
- Callback này thuộc task, microtask hay render frame?
- Promise chain có tạo microtask loop làm starve render/timer không?
- Timer delay là do timeout value hay event loop đang bị block?
- UI freeze do CPU work, layout/render hay network wait?
- Node.js service có event loop lag vì CPU/blocking I/O không?
- Có cần Web Worker/Worker Thread hoặc chunking work không?

## Failure Modes / Cách nó gây lỗi

- Long synchronous loop làm browser UI đơ và input delay tăng.
- Microtask chain quá dài làm render/timer bị trì hoãn.
- Hiểu sai thứ tự promise/timer làm test flaky hoặc logic race.
- Blocking CPU trong Node.js làm mọi request khác chậm dù I/O async.
- Unhandled rejection xảy ra ngoài call stack ban đầu nên khó trace.
- Debounce/throttle sai làm event xử lý trễ hoặc quá nhiều.

## Khi nào chưa cần hoặc dễ over-engineer

- Trang đơn giản ít async/performance issue có thể chưa cần phân tích event loop sâu.
- Không nên thêm worker hoặc queue nếu bottleneck thật là network/API hoặc query chậm.
- Không nên tối ưu microtask/task ordering nếu UX và metric chưa có vấn đề.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì event loop là cơ chế runtime lõi của JavaScript async.
- [[Runtime]] vì event loop thuộc behavior của runtime chứ không chỉ syntax.
- [[CSR]] vì client-side rendering phụ thuộc main thread/event loop của browser.
- [[Thread Starvation]] vì event loop blocked/starved có triệu chứng giống worker starvation.
- [[Performance Optimization]] vì long task/event loop lag ảnh hưởng trực tiếp UX/throughput.

## Liên quan rộng

- Frontend engineering
- Browser runtime
- Node.js runtime
- User experience

## Keywords / Từ khóa tìm kiếm

- Event Loop
- event loop
- microtask
- task queue
- vòng lặp sự kiện
- JavaScript event loop
- promise microtask
- setTimeout order
- long task
- event loop lag
- main thread blocking
- Node.js event loop
- async race
- event loop debugging

## Source trace

- MDN Web Docs
- WHATWG HTML event loop
- Node.js event loop documentation
