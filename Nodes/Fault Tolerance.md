# Fault Tolerance

Aliases: fault-tolerant system, chịu lỗi

Type: Reliability / SRE

## Context / Ngữ cảnh

Fault Tolerance xuất hiện khi hệ thống cần tiếp tục phục vụ dù một phần bị lỗi.

## Boundary / Ranh giới

### Nó là gì

Fault Tolerance là khả năng phát hiện, cô lập và phục hồi từ fault mà không làm toàn hệ thống fail.

### Nó không phải là gì

Nó không phải không bao giờ lỗi và không thay thế monitoring/incident response.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là redundancy, timeout, retry, failover, isolation và recovery.

## Project Role / Vai trò trong dự án

Node này giúp thiết kế service, data system và operation có failure plan rõ.

## Output / Artifact nên có

- Fault model: crash, timeout, data loss, dependency down
- Failover/degradation plan
- Recovery test hoặc game-day checklist

## Decision Checklist / Câu hỏi kiểm tra

- Fault nào được chấp nhận và fault nào không?
- Failover có tự động hay thủ công?
- Recovery có giữ data consistency không?

## Failure Modes / Cách nó gây lỗi

- Redundancy cùng failure domain
- Failover chưa test nên chỉ là giả định
- Retry/fallback làm lỗi lan rộng hơn

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần HA phức tạp cho prototype không user thật
- Dễ over-engineer nếu target reliability thấp nhưng architecture quá nhiều moving parts

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Distributed System]] vì fault độc lập là vấn đề lõi
- [[Reliability]] vì fault tolerance là chiến lược tăng reliability

## Liên quan rộng

- Redundancy
- Failover

## Keywords / Từ khóa tìm kiếm

- Fault Tolerance
- failure handling
- redundancy
- graceful degradation
- failover
- resilience
- chịu lỗi

## Source trace

- DDIA
- Google SRE Books
