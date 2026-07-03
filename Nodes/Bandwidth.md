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

- Bandwidth baseline theo path
- Payload-size và transfer-rate metric
- Network capacity note cho replication/media

## Decision Checklist / Câu hỏi kiểm tra

- Giới hạn là bandwidth hay latency?
- Payload nào đang chiếm băng thông?
- Path có shared link hoặc egress cap không?

## Failure Modes / Cách nó gây lỗi

- Link saturated làm latency tăng
- Replication lag do bandwidth chứ không phải DB
- Tối ưu CPU trong khi payload quá lớn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu payload nhỏ và traffic thấp
- Dễ over-engineer nếu compression/CDN không tác động user rõ

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Throughput]] vì bandwidth là throughput ở network path
- [[CDN]] vì CDN có thể giảm bandwidth tới origin

## Liên quan rộng

- Network capacity

## Source trace

- Computer Networks Map
