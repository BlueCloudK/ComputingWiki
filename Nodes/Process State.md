# Process State

Aliases: process lifecycle state, trạng thái tiến trình

Type: Operating System

## Context / Ngữ cảnh

Process State xuất hiện khi cần hiểu process đang running, ready, blocked, waiting hay terminated.

## Boundary / Ranh giới

### Nó là gì

Process State là trạng thái lifecycle của process trong scheduler/OS.

### Nó không phải là gì

Nó không phải state domain của app.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là OS chuyển process giữa state theo CPU, IO và event.

## Project Role / Vai trò trong dự án

Node này giúp debug hang, blocked process, resource wait và scheduling behavior.

## Output / Artifact nên có

- Observed process state: running, ready, blocked, sleeping, zombie
- Wait reason: CPU, IO, lock, child process
- Command/log evidence khi process hang

## Decision Checklist / Câu hỏi kiểm tra

- Process đang chờ CPU, IO, lock hay signal?
- State thay đổi theo thời gian hay stuck?
- Có child/zombie process cần reap không?

## Failure Modes / Cách nó gây lỗi

- Gọi app 'crash' khi process chỉ blocked
- Không phân biệt CPU-bound với IO-wait
- Zombie process tích tụ vì parent không reap

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu app không có symptom runtime/process
- Dễ over-engineer nếu dùng process-state analysis cho bug logic thuần

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Process]] vì state là lifecycle của process
- [[Scheduling]] vì scheduler dựa trên state để chọn process

## Liên quan rộng

- Runtime debugging

## Keywords / Từ khóa tìm kiếm

- Process State
- running ready blocked
- process lifecycle
- scheduler state
- waiting state
- trạng thái tiến trình

## Source trace

- Operating Systems Map
