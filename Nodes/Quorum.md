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

- [[Replication]] vì quorum thường dùng trong replicated data
- [[Consensus]] vì consensus cần agreement threshold

## Liên quan rộng

- Majority
- Read/write quorum

## Source trace

- DDIA Ch05-Ch09
