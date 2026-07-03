# Capacity

Aliases: system capacity, năng lực hệ thống

Type: Performance / Scalability

## Context / Ngữ cảnh

Capacity xuất hiện khi cần biết giới hạn phục vụ của hệ thống trước khi degradation hoặc failure xảy ra.

## Boundary / Ranh giới

### Nó là gì

Capacity là lượng workload hệ thống xử lý được trong điều kiện và SLO cụ thể.

### Nó không phải là gì

Nó không phải throughput đơn lẻ nếu không kèm latency/error target.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là giới hạn bởi bottleneck, resource headroom, dependency limit và scaling policy.

## Project Role / Vai trò trong dự án

Node này giúp trả lời hệ thống chịu được bao nhiêu user/request/event trước khi cần scale.

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

- [[Capacity Planning]] vì planning dựa trên capacity hiện tại/tương lai
- [[Throughput]] vì throughput là một mặt của capacity

## Liên quan rộng

- Headroom
- Load limits

## Source trace

- Google SRE Books
- DDIA Ch01
