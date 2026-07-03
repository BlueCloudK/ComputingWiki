# Performance Budget

Aliases: performance budget, ngân sách hiệu năng

Type: Performance / Scalability

## Context / Ngữ cảnh

Performance Budget xuất hiện khi team cần giới hạn latency, size, CPU, memory hoặc network cost để tránh chậm dần theo thời gian.

## Boundary / Ranh giới

### Nó là gì

Performance Budget là target hoặc limit định lượng cho một flow hoặc artifact.

### Nó không phải là gì

Nó không phải tối ưu mọi thứ và không thay thế benchmark/profiling.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là đặt ngưỡng, đo trong CI/monitoring và chặn hoặc cảnh báo khi vượt budget.

## Project Role / Vai trò trong dự án

Node này giúp performance trở thành constraint thiết kế thay vì xử lý muộn.

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

- [[Latency]] vì latency thường có budget
- [[Benchmark]] vì budget cần đo lặp lại

## Liên quan rộng

- Web performance
- Release gates

## Source trace

- Google SRE Books
- Performance engineering references
