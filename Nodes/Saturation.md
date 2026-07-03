# Saturation

Aliases: resource saturation, bão hòa tài nguyên

Type: Performance / Scalability

## Context / Ngữ cảnh

Saturation xuất hiện khi resource gần hoặc vượt khả năng phục vụ làm latency/error tăng.

## Boundary / Ranh giới

### Nó là gì

Saturation là mức độ tài nguyên như CPU, memory, disk, thread pool, DB connection hoặc queue bị dùng hết.

### Nó không phải là gì

Nó không phải utilization bình thường nếu chưa có queue/error impact.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là demand vượt service capacity khiến queue, wait time hoặc rejection tăng.

## Project Role / Vai trò trong dự án

Node này giúp phát hiện bottleneck thật trong performance/capacity planning.

## Output / Artifact nên có

- Saturation metric cho CPU, memory, disk, pool, queue
- Headroom threshold
- Runbook khi resource gần full

## Decision Checklist / Câu hỏi kiểm tra

- Resource nào đang gần max?
- Saturation có đi kèm queue/latency/error không?
- Scale resource đó có giảm bottleneck không?

## Failure Modes / Cách nó gây lỗi

- CPU thấp nhưng DB pool/thread pool saturated
- Disk đầy làm write fail
- Queue saturated làm latency tăng dây chuyền

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu chưa có load/resource pressure
- Dễ over-engineer nếu chỉ nhìn utilization mà không có user impact

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Bottleneck]] vì saturated resource thường là bottleneck
- [[Capacity Planning]] vì capacity cần headroom trước saturation

## Liên quan rộng

- Utilization
- Resource limits

## Source trace

- Google SRE Books
- Systems Performance
