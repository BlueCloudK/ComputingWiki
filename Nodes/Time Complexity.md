# Time Complexity

Aliases: time cost, độ phức tạp thời gian

Type: Computer Foundation

## Context / Ngữ cảnh

Time Complexity xuất hiện khi cần hiểu runtime tăng thế nào khi input size tăng.

## Boundary / Ranh giới

### Nó là gì

Time Complexity mô tả growth của số bước hoặc thao tác theo kích thước input.

### Nó không phải là gì

Nó không phải benchmark thực tế và không thay thế đo production performance.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là mô hình hóa cost theo n, thường bằng Big O để so sánh growth.

## Project Role / Vai trò trong dự án

Node này giúp chọn algorithm/data structure trước khi data tăng làm hệ thống chậm.

## Output / Artifact nên có

- Complexity statement theo n cụ thể
- Worst/average/amortized note nếu quan trọng
- Input-size threshold khiến algorithm cần đổi

## Decision Checklist / Câu hỏi kiểm tra

- n trong bài này là item, edge, byte hay request?
- Worst-case có xảy ra trong dữ liệu thật không?
- Có hidden nested loop hoặc repeated query không?

## Failure Modes / Cách nó gây lỗi

- Ghi O(n) nhưng mỗi bước lại gọi query/network
- Tối ưu constant nhỏ trong khi growth sai
- Dùng average-case cho input attacker-controlled

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu input nhỏ và bounded
- Dễ over-engineer nếu complexity không nằm trên hot path hoặc đã được đo là ổn

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Big O Notation]] vì Big O là notation chính
- [[Benchmark]] vì complexity cần đối chiếu với đo thực tế

## Liên quan rộng

- Algorithm analysis
- Scalability reasoning

## Keywords / Từ khóa tìm kiếm

- Time Complexity
- algorithm runtime
- Big O time
- worst case time
- asymptotic time
- độ phức tạp thời gian

## Source trace

- Algorithms Map
- CLRS
