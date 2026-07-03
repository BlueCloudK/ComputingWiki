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

- Decision note hoặc checklist ngắn khi concept này ảnh hưởng thiết kế/debug.
- Test, metric, diagram hoặc config liên quan nếu concept nằm trên critical path.

## Decision Checklist / Câu hỏi kiểm tra

- Concept này đang giải quyết constraint cụ thể nào?
- Boundary của nó nằm ở code, runtime, network, data hay operations?
- Có metric, test hoặc source trace đủ để kiểm chứng không?

## Failure Modes / Cách nó gây lỗi

- Dùng concept đúng tên nhưng sai boundary nên debug lệch hướng.
- Thiếu metric/test làm lỗi chỉ lộ khi scale hoặc deploy thật.
- Overfit vào tool cụ thể thay vì hiểu cơ chế ổn định phía sau.

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần đào sâu nếu hệ thống nhỏ và chưa chạm constraint liên quan.
- Dễ over-engineer nếu thêm abstraction/process trước khi có failure mode thật.

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
