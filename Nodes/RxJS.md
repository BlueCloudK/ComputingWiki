# RxJS

Aliases: RxJS, Reactive Extensions for JavaScript

Type: Frontend Framework

## Context / Ngữ cảnh

RxJS xuất hiện khi JavaScript app cần xử lý nhiều luồng event/asynchronous data như user input, WebSocket, timer, stream hoặc state phức tạp theo kiểu reactive.

## Boundary / Ranh giới

### Nó là gì

RxJS là thư viện reactive programming cho JavaScript, dùng Observable và operator để mô hình hóa, biến đổi, combine và cancel stream dữ liệu theo thời gian.

### Nó không phải là gì

RxJS không phải state manager bắt buộc cho mọi frontend app. Với flow async đơn giản, Promise/state thường đủ dễ hiểu hơn.

## Core Mechanism / Cơ chế lõi

Observable phát value/error/complete theo thời gian. Subscriber nhận value; operator như map, filter, switchMap, debounceTime, mergeMap biến đổi hoặc kết hợp stream. Subscription cần được cleanup để tránh leak.

## Project Role / Vai trò trong dự án

Dùng node này khi debug event stream, autocomplete debounce, WebSocket flow, cancellation, race condition hoặc memory leak do subscription.

## Output / Artifact nên có

- Observable source map
- Operator chain rõ mục đích
- Subscription cleanup rule
- Error handling path
- Test marble hoặc behavior test nếu flow quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Data này có thật sự là stream theo thời gian không?
- Operator nào chịu trách nhiệm cancel/race?
- Subscription được cleanup ở đâu?
- Error có làm stream chết ngoài ý muốn không?
- Có thể viết đơn giản hơn bằng Promise/state không?

## Failure Modes / Cách nó gây lỗi

- Quên unsubscribe gây memory leak.
- Chọn mergeMap/switchMap sai làm race hoặc cancel nhầm.
- Operator chain quá dài khó debug.
- Error không catch làm stream dừng.
- Dùng RxJS cho case quá đơn giản làm code khó đọc.

## Khi nào chưa cần hoặc dễ over-engineer

- Async request đơn giản có thể dùng Promise/fetch hoặc data fetching library.
- Không nên đưa RxJS vào toàn app nếu chỉ có vài event đơn giản.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[JavaScript]] vì RxJS chạy trong JavaScript ecosystem.
- [[Memory Leak]] vì subscription không cleanup dễ gây leak.
- [[Event Loop]] vì stream async vẫn chạy trên event loop/runtime.
- [[State Management]] vì RxJS đôi khi dùng để mô hình hóa state/event stream.

## Liên quan rộng

- Reactive programming
- Event stream
- Async cancellation

## Keywords / Từ khóa tìm kiếm

- RxJS
- Reactive Extensions for JavaScript
- Observable
- subscription
- switchMap
- mergeMap
- debounceTime
- RxJS debugging

## Source trace

- RxJS documentation
- MDN Web Docs
