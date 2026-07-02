# TCP

Aliases: Transmission Control Protocol, giao thức TCP

## Dùng trong dự án để làm gì

TCP liên quan tới cách các máy, service hoặc client giao tiếp qua mạng. Khi hệ thống gọi API, truyền message, debug timeout hoặc thiết kế integration, node này giúp hiểu lớp giao tiếp đang có vấn đề ở đâu.

## Khi nào cần quan tâm

- API call timeout, retry nhiều hoặc kết nối chập chờn
- Thiết kế giao tiếp giữa service/client
- Cần debug protocol, routing hoặc DNS

## Lỗi / rủi ro thường gặp

- Timeout/retry không rõ làm lỗi lan rộng
- Client và server hiểu khác protocol hoặc version
- Debug sai tầng nên mất thời gian ở chỗ không liên quan

## Gồm những gì

- [[Reliable Data Transfer]]
- [[Flow Control]]
- [[Congestion Control]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Computer Networks Map / Ch03.5
