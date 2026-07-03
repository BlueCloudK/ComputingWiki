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

- Socket endpoint: protocol, address, port
- Timeout/retry setting
- Connection lifecycle note

## Decision Checklist / Câu hỏi kiểm tra

- Socket đang connect, listen hay accept?
- Timeout là connect, read hay idle timeout?
- Có leak socket/file descriptor không?

## Failure Modes / Cách nó gây lỗi

- Connection refused do không listen
- Socket leak làm hết file descriptor
- Timeout bị hiểu nhầm thành business failure

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu HTTP client abstraction đã đủ
- Dễ over-engineer nếu không cần network-programming layer

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Port]] vì socket dùng port để bind/connect
- [[TCP]] vì TCP socket là abstraction phổ biến

## Liên quan rộng

- Network programming

## Keywords / Từ khóa tìm kiếm

- Socket
- network socket
- TCP socket
- UDP socket
- client socket
- server socket
- socket connection
- kết nối socket

## Source trace

- Computer Networks Map
