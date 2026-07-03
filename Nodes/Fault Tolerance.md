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

- [[Distributed System]] vì fault độc lập là vấn đề lõi
- [[Reliability]] vì fault tolerance là chiến lược tăng reliability

## Liên quan rộng

- Redundancy
- Failover

## Source trace

- DDIA
- Google SRE Books
