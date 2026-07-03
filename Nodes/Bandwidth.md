# Bandwidth

Aliases: network bandwidth, băng thông

Type: Performance / Scalability

## Context / Ngữ cảnh

Bandwidth xuất hiện khi throughput network bị giới hạn bởi dung lượng truyền dữ liệu.

## Boundary / Ranh giới

### Nó là gì

Bandwidth là lượng bit/byte có thể truyền qua network path trong một đơn vị thời gian.

### Nó không phải là gì

Nó không phải latency dù thường bị nhầm.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là capacity của link/path chịu ảnh hưởng congestion, sharing và protocol overhead.

## Project Role / Vai trò trong dự án

Node này giúp debug upload/download chậm, replication lag hoặc media delivery.

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

- [[Throughput]] vì bandwidth là throughput ở network path
- [[CDN]] vì CDN có thể giảm bandwidth tới origin

## Liên quan rộng

- Network capacity

## Source trace

- Computer Networks Map
