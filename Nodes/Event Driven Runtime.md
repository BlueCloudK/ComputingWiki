# Event Driven Runtime

Aliases: Event Driven Runtime, event-driven runtime

Type: Programming Languages Deep

## Context / Ngữ cảnh

Event Driven Runtime xuất hiện khi chương trình chạy bằng cách phản ứng với event như I/O, timer, user input, message hoặc callback thay vì chạy tuyến tính từ đầu đến cuối.

## Boundary / Ranh giới

### Nó là gì

Event Driven Runtime là runtime tổ chức execution quanh event loop/dispatcher, callback/task queue và handler để xử lý công việc bất đồng bộ.

### Nó không phải là gì

Event Driven Runtime không tự đồng nghĩa với parallel processing. Một event loop có thể xử lý nhiều I/O concurrency nhưng vẫn chạy handler trên một thread chính.

## Core Mechanism / Cơ chế lõi

Runtime nhận event từ OS/network/timer/UI, đưa vào queue, chọn handler phù hợp và execute. Handler nên ngắn, không block event loop và trả quyền điều khiển để runtime tiếp tục xử lý event khác.

## Project Role / Vai trò trong dự án

Dùng node này khi debug Node.js/UI runtime, callback delay, event loop block, async race, timer behavior hoặc throughput của service nhiều I/O.

## Output / Artifact nên có

- Event source list
- Queue/loop model
- Handler latency metric
- Blocking operation audit
- Trace/log cho event flow

## Decision Checklist / Câu hỏi kiểm tra

- Event nào kích hoạt handler?
- Handler có block event loop không?
- Work nặng có được chuyển sang worker/background không?
- Error async có được handle không?
- Queue backlog/latency có metric không?

## Failure Modes / Cách nó gây lỗi

- Handler CPU nặng làm mọi event khác chậm.
- Async error bị nuốt hoặc crash process.
- Callback order bị hiểu sai tạo race.
- Timer không chính xác khi loop bị block.
- Backpressure thiếu làm queue phình.

## Khi nào chưa cần hoặc dễ over-engineer

- Script đồng bộ nhỏ chưa cần mô hình event runtime sâu.
- Không nên dùng event-driven architecture nếu workflow tuần tự đơn giản dễ đọc hơn.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Event Loop]] vì event-driven runtime thường dựa trên event loop.
- [[Runtime]] vì đây là một mô hình runtime execution.
- [[Backpressure]] vì event queue cần kiểm soát khi producer nhanh hơn consumer.
- [[Thread Starvation]] vì handler/blocking work có thể làm runtime không xử lý event kịp.

## Liên quan rộng

- Async programming
- Callback
- I/O concurrency

## Keywords / Từ khóa tìm kiếm

- Event Driven Runtime
- event-driven runtime
- event loop
- callback queue
- async runtime
- I/O event
- event driven runtime debugging

## Source trace

- Node.js documentation
- MDN Web Docs
- Crafting Interpreters
