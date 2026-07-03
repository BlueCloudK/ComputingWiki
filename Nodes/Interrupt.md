# Interrupt

Aliases: hardware interrupt, ngắt

Type: Operating System

## Context / Ngữ cảnh

Interrupt xuất hiện khi hardware/timer/event cần CPU dừng luồng hiện tại để xử lý sự kiện.

## Boundary / Ranh giới

### Nó là gì

Interrupt là signal chuyển control tới handler để xử lý event ưu tiên.

### Nó không phải là gì

Nó không phải exception business hay callback app.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là CPU lưu context, chạy interrupt handler rồi quay lại execution.

## Project Role / Vai trò trong dự án

Node này giúp hiểu IO, scheduling, latency thấp tầng và device interaction.

## Output / Artifact nên có

- Interrupt source: timer, device, software
- Handler/latency note
- Evidence từ OS/device logs khi debug

## Decision Checklist / Câu hỏi kiểm tra

- Event này là interrupt, polling hay callback app?
- Handler có làm việc quá lâu không?
- Interrupt rate có gây latency hoặc CPU spike không?

## Failure Modes / Cách nó gây lỗi

- Interrupt storm làm CPU cao
- Handler chậm gây mất event/latency
- Nhầm interrupt với exception business

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không debug OS/embedded/device/perf thấp tầng
- Dễ over-engineer nếu app-level async callback bị gọi là interrupt

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Device Driver]] vì driver thường xử lý interrupt từ thiết bị
- [[Scheduling]] vì timer interrupt hỗ trợ preemption

## Liên quan rộng

- Hardware events

## Keywords / Từ khóa tìm kiếm

- Interrupt
- hardware interrupt
- interrupt handler
- asynchronous event
- I/O interrupt
- ngắt hệ thống

## Source trace

- Operating Systems Map
