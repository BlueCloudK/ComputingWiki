# ANR

Aliases: ANR, Application Not Responding

Type: Mobile Development

## Context / Ngữ cảnh

ANR xuất hiện trong Android khi app không phản hồi kịp với input, lifecycle event hoặc broadcast, khiến hệ thống báo ứng dụng không phản hồi.

## Boundary / Ranh giới

### Nó là gì

ANR là trạng thái Android báo app bị kẹt hoặc quá chậm trên main thread trong một khoảng thời gian quan trọng.

### Nó không phải là gì

ANR không giống crash. App có thể vẫn còn chạy, nhưng UI bị chặn và user không thao tác được.

## Core Mechanism / Cơ chế lõi

Nếu main thread bị block bởi CPU work, disk I/O, network call, lock hoặc deadlock, app không xử lý input/lifecycle đúng hạn và hệ thống ghi nhận ANR.

## Project Role / Vai trò trong dự án

Dùng node này khi debug app treo, UI đơ, thao tác chậm, thread dump hoặc performance issue trên Android.

## Output / Artifact nên có

- ANR trace/thread dump
- Main thread blocking analysis
- Reproduction step
- Startup/input responsiveness metric
- Fix note: move work off main thread, timeout, async boundary

## Decision Checklist / Câu hỏi kiểm tra

- Main thread đang làm việc nặng gì?
- Có network/disk/lock trên main thread không?
- ANR xảy ra ở startup, input hay background receiver?
- Có trace đủ để thấy call stack không?
- Việc nặng có thể tách sang background/coroutine phù hợp không?

## Failure Modes / Cách nó gây lỗi

- Network hoặc disk I/O chạy trên main thread.
- Deadlock làm UI không phản hồi.
- Vòng lặp CPU nặng chặn input.
- Startup quá nặng khiến app treo khi mở.
- Background callback quay lại main thread quá lâu.

## Khi nào chưa cần hoặc dễ over-engineer

- App chưa có Android runtime path thì chưa cần tối ưu ANR.
- Không nên tối ưu mù nếu chưa có trace hoặc reproduction.

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Kotlin]] vì nhiều Android app gây/giải ANR bằng Kotlin code.
- [[Thread Starvation]] vì main thread bị block là dạng starvation ở UI thread.
- [[Performance Optimization]] vì ANR là failure nghiêm trọng về responsiveness.
- [[APK]] vì ANR thường được debug trên artifact Android đã build/cài.

## Liên quan rộng

- Android performance
- Main thread
- Mobile reliability

## Keywords / Từ khóa tìm kiếm

- ANR
- Application Not Responding
- Android ANR
- main thread blocked
- thread dump
- UI freeze
- ANR debugging

## Source trace

- Android Developers documentation
