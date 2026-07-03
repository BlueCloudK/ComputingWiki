# CAP Theorem

Aliases: CAP, định lý CAP

Type: Data / Database

## Context / Ngữ cảnh

CAP Theorem xuất hiện khi phân tích trade-off của distributed data system dưới network partition.

## Boundary / Ranh giới

### Nó là gì

CAP Theorem nói khi có partition, hệ thống phải trade-off giữa consistency và availability theo nghĩa formal.

### Nó không phải là gì

Nó không phải checklist chọn database đơn giản và không mô tả mọi trade-off thực tế.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là partition làm node không giao tiếp được; system phải chọn reject/wait hoặc trả dữ liệu có thể không nhất quán.

## Project Role / Vai trò trong dự án

Node này giúp tránh tuyên bố mơ hồ kiểu database vừa CP vừa AP trong mọi tình huống.

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

- [[Distributed System]] vì CAP chỉ có ý nghĩa trong distributed system
- [[Consistency]] vì consistency là một cạnh của trade-off

## Liên quan rộng

- Network partition
- Availability trade-off

## Source trace

- DDIA Ch09
