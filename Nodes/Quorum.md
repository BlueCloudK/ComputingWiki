# Quorum

Aliases: quorum, số phiếu tối thiểu

Type: Data / Database

## Context / Ngữ cảnh

Quorum xuất hiện khi distributed system cần quyết định dựa trên đủ số node để cân bằng consistency và availability.

## Boundary / Ranh giới

### Nó là gì

Quorum là ngưỡng số replica/node cần đồng ý hoặc phản hồi để operation được xem là hợp lệ.

### Nó không phải là gì

Nó không phải majority trong mọi thiết kế và không tự đảm bảo correctness nếu protocol sai.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là chọn read/write/decision threshold sao cho các tập node giao nhau theo guarantee mong muốn.

## Project Role / Vai trò trong dự án

Node này giúp hiểu replication, consensus và availability trade-off.

## Output / Artifact nên có

- Read/write quorum formula
- Replica count và failure tolerance note
- Behavior khi thiếu quorum

## Decision Checklist / Câu hỏi kiểm tra

- Quorum cần majority hay threshold khác?
- Read/write quorum có giao nhau không?
- Khi không đủ quorum thì reject hay stale read?

## Failure Modes / Cách nó gây lỗi

- Quorum config không giao nhau làm mất consistency
- Chờ quá nhiều replica làm latency cao
- Không tính failure domain nên quorum sống trên cùng AZ

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu không có replicated data/consensus
- Dễ over-engineer nếu consistency requirement thấp hơn cost quorum

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Replication]] vì quorum thường dùng trong replicated data
- [[Consensus]] vì consensus cần agreement threshold

## Liên quan rộng

- Majority
- Read/write quorum

## Keywords / Từ khóa tìm kiếm

- Quorum
- read quorum
- write quorum
- majority vote
- replication quorum
- consensus quorum
- số phiếu tối thiểu

## Source trace

- DDIA Ch05-Ch09
