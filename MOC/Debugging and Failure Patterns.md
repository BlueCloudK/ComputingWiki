# Debugging and Failure Patterns

Aliases: failure patterns, debugging patterns, mẫu lỗi hệ thống

Type: Debugging / Reliability

## Context / Ngữ cảnh

Debugging and Failure Patterns gom các lỗi vận hành và lỗi thiết kế thường gặp khi hệ thống chạy thật, scale lên hoặc phụ thuộc nhiều service.

## Boundary / Ranh giới

### Nó là gì

Debugging and Failure Patterns là MOC điều hướng tới các node cụ thể trong cùng vùng kiến thức.

### Nó không phải là gì

Nó không thay thế node chi tiết và không phải nơi viết tutorial dài.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom node theo pack để tìm kiếm, học và mở rộng graph có kiểm soát.

## Project Role / Vai trò trong dự án

Debugging and Failure Patterns giúp mở rộng ComputingWiki theo breadth mà vẫn giữ graph đọc được trong Obsidian.

## Output / Artifact nên có

- Danh sách node con cùng pack
- Keyword điều hướng tìm kiếm
- Source trace cấp vùng kiến thức

## Decision Checklist / Câu hỏi kiểm tra

- Node mới có thuộc vùng Debugging and Failure Patterns thật không?
- Có nên tạo node riêng hay chỉ là keyword/alias?
- Link trong MOC có giúp đi từ vùng lớn xuống node cụ thể không?

## Failure Modes / Cách nó gây lỗi

- Nhồi tool hoặc keyword không liên quan làm graph nhiễu
- Link ngang quá rộng khiến MOC mất vai trò điều hướng
- Tạo node quá nhỏ trước khi có source trace hoặc nhu cầu đọc rõ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tách sâu nếu pack chỉ có vài node và chưa dùng để học/debug
- Dễ over-engineer nếu biến MOC thành tutorial hoặc danh sách tool quá chi tiết

## Gồm những gì

- [[Timeout]]
- [[Retry]]
- [[Exponential Backoff]]
- [[Retry Storm]]
- [[Circuit Breaker]]
- [[Memory Leak]]
- [[Connection Leak]]
- [[Thread Starvation]]
- [[Resource Exhaustion]]
- [[Queue Backlog]]
- [[Thundering Herd]]
- [[Cache Stampede]]
- [[Stale Cache]]
- [[Config Drift]]
- [[N Plus One Query]]
- [[Split Brain]]
- [[Log Correlation]]
- [[Trace ID]]
- [[Distributed Tracing]]
- [[Stack Trace]]
- [[Heap Dump]]
- [[Thread Dump]]
- [[Core Dump]]
- [[Incident Timeline]]
- [[Root Cause Analysis]]
- [[Error Rate]]
- [[Alert Fatigue]]
- [[Flaky Test]]
- [[Livelock]]
- [[Partial Failure]]
- [[Cascading Failure]]
- [[Data Corruption]]
- [[Clock Skew]]
- [[Time Drift]]
- [[Dependency Failure]]
- [[Brownout]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- ComputingWiki breadth expansion
- Search and navigation
- Obsidian graph hygiene

## Keywords / Từ khóa tìm kiếm

- Debugging and Failure Patterns
- failure patterns
- debugging patterns
- mẫu lỗi hệ thống
- Debugging and Failure Patterns MOC
- debugging and failure patterns map
- mục lục kiến thức
- nhánh kiến thức
- Timeout
- Retry
- Exponential Backoff
- Retry Storm
- Circuit Breaker
- Memory Leak

## Source trace

- Google SRE Book
- Release It!
- Designing Data-Intensive Applications
