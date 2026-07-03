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

- [[Big O Notation]] vì Big O là notation chính
- [[Benchmark]] vì complexity cần đối chiếu với đo thực tế

## Liên quan rộng

- Algorithm analysis
- Scalability reasoning

## Source trace

- Algorithms Map
- CLRS
