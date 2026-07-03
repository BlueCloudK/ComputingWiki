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

- Budget table: latency, bundle size, memory, CPU, query count
- CI/release gate cho budget
- Owner và exception process

## Decision Checklist / Câu hỏi kiểm tra

- Budget gắn với user journey nào?
- Đo bằng lab, CI hay production?
- Vượt budget thì block release hay warn?

## Failure Modes / Cách nó gây lỗi

- Budget đặt tùy tiện không gắn user impact
- Metric đo không ổn định làm gate nhiễu
- Exception tích tụ làm budget vô nghĩa

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần nếu chưa có flow critical hoặc baseline
- Dễ over-engineer nếu budget nhiều hơn khả năng đo/duy trì

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
