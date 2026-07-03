# CAP Theorem

Aliases: CAP, định lý CAP, Brewer theorem, CAP tradeoff

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

- Partition behavior decision note
- Consistency vs availability trade-off record
- Database guarantee note trong tình huống partition

## Decision Checklist / Câu hỏi kiểm tra

- Khi network partition, hệ thống reject/wait hay trả dữ liệu có thể stale?
- Consistency đang nói linearizability hay consistency kiểu khác?
- Availability cần cho operation nào?

## Failure Modes / Cách nó gây lỗi

- Hiểu sai thành 'chọn 2 trong 3' mọi lúc
- Dùng CAP thay cho phân tích latency/consistency cụ thể
- Gọi database CP/AP nhưng không nói operation và partition behavior

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần bàn sâu nếu app dùng một DB đơn giản không phân tán
- Dễ over-engineer nếu dùng CAP để quyết định khi requirement thật chỉ là backup/latency

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Distributed System]] vì CAP chỉ có ý nghĩa trong distributed system
- [[Consistency]] vì consistency là một cạnh của trade-off

## Liên quan rộng

- Network partition
- Availability trade-off

## Keywords / Từ khóa tìm kiếm

- CAP Theorem
- consistency availability partition tolerance
- network partition
- CP AP trade-off
- distributed database trade-off
- stale read
- consistency trade-off
- định lý CAP
- đánh đổi nhất quán sẵn sàng

## Source trace

- DDIA Ch09
