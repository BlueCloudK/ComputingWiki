# CDN

Aliases: Content Delivery Network, mạng phân phối nội dung

Type: Architecture / System Design

## Context / Ngữ cảnh

CDN xuất hiện khi static/media/web content cần được phục vụ gần user hơn và giảm tải origin.

## Boundary / Ranh giới

### Nó là gì

CDN là mạng edge cache/proxy phân phối content từ location gần user.

### Nó không phải là gì

Nó không phải database cache và không tự sửa API chậm.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là cache/serve content từ edge dựa trên URL, headers và invalidation policy.

## Project Role / Vai trò trong dự án

Node này giúp cải thiện latency/bandwidth cho asset và bảo vệ origin khỏi traffic spike.

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

- [[Cache]] vì CDN là cache ở network edge
- [[HTTPS]] vì CDN thường terminate/proxy HTTPS

## Liên quan rộng

- Edge delivery
- Static assets

## Source trace

- Computer Networks Map
- Cloud architecture docs
