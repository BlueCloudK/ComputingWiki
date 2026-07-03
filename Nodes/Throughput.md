# Throughput

Aliases: processing rate, thông lượng

Type: Performance / Scalability

## Context / Ngữ cảnh

Throughput xuất hiện khi cần biết hệ thống xử lý được bao nhiêu request, event, job hoặc byte trong một đơn vị thời gian.

## Boundary / Ranh giới

### Nó là gì

Throughput là tốc độ hoàn thành work của hệ thống, ví dụ requests per second, messages per second hoặc rows per hour.

### Nó không phải là gì

Nó không phải latency. Hệ thống có throughput cao vẫn có thể làm từng user chờ lâu nếu queue hoặc tail latency lớn.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là capacity của pipeline: arrival rate, service rate, bottleneck và parallelism. Khi arrival rate vượt service rate, queue tăng và latency xấu đi.

## Project Role / Vai trò trong dự án

Throughput giúp capacity planning, load test và scaling decision. Nó trả lời hệ thống có đủ sức xử lý volume hiện tại/tương lai không.

## Output / Artifact nên có

- Throughput baseline và peak target
- Bottleneck hoặc saturation point
- Scaling/capacity note cho workload quan trọng

## Decision Checklist / Câu hỏi kiểm tra

- Work unit là request, event, job hay byte?
- Throughput cần cho average hay peak load?
- Bottleneck hiện tại nằm ở đâu?
- Scale thêm worker có tăng throughput thật không?
- Throughput tăng có làm latency hoặc error rate xấu đi không?

## Failure Modes / Cách nó gây lỗi

- Chỉ tăng concurrency làm DB/external service nghẽn
- Đo throughput mà không đo error rate/latency kèm theo
- Capacity planning dựa trên average, bỏ qua peak
- Không có backpressure khi producer nhanh hơn consumer

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tối ưu throughput nếu volume thấp và không tăng nhanh
- Dễ over-engineer nếu scale trước khi tìm bottleneck thật

## Gồm những gì

- Chưa tách nhánh

## Nối mạnh

- [[Load]] vì throughput phải được hiểu dưới workload cụ thể
- [[Capacity Planning]] vì capacity dựa nhiều vào throughput target
- [[Backpressure]] vì throughput mismatch cần cơ chế điều tiết flow

## Liên quan rộng

- Processing rate
- Scaling
- Queueing

## Keywords / Từ khóa tìm kiếm

- Throughput
- processing rate
- thông lượng
- Performance
- Scalability

## Source trace

- Designing Data-Intensive Applications Ch01
- Google SRE Books
