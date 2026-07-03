# Socket

Aliases: network socket, socket

Type: Protocol / Data Format

## Context / Ngữ cảnh

Socket xuất hiện khi program giao tiếp qua network bằng endpoint IP/port/protocol.

## Boundary / Ranh giới

### Nó là gì

Socket là OS abstraction cho send/receive data qua TCP/UDP hoặc domain socket.

### Nó không phải là gì

Nó không phải WebSocket riêng và không phải API contract đầy đủ.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là bind/listen/connect/send/receive trên endpoint.

## Project Role / Vai trò trong dự án

Node này giúp hiểu server listen, client connect, timeout và connection errors.

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

- [[Port]] vì socket dùng port để bind/connect
- [[TCP]] vì TCP socket là abstraction phổ biến

## Liên quan rộng

- Network programming

## Source trace

- Computer Networks Map
