# Delay Loss and Throughput

Aliases: network delay/loss/throughput, độ trễ mất gói thông lượng

Type: Performance / Scalability

## Bản chất

Delay Loss and Throughput liên quan tới tốc độ, throughput, resource usage hoặc khả năng chịu tải khi dữ liệu/user tăng. Điểm chính là phải đo được bằng metric và workload thật, không tối ưu theo cảm giác. Nó nối với các phần liên quan như [[Computer Performance]] và nhóm quyết định quanh delay loss and throughput.

## Dùng trong dự án để làm gì

Delay Loss and Throughput giúp đặt baseline, benchmark/load test, tìm bottleneck và chọn trade-off giữa performance, cost và complexity. Trong dự án, nó quyết định khi nào cần index/cache/scale/refactor.

## Khi nào cần quan tâm

- Response time, throughput hoặc resource usage vượt ngưỡng
- Traffic/data tăng nhanh hoặc chuẩn bị release lớn
- Cần so sánh trước/sau một thay đổi tối ưu
- Chi phí hạ tầng tăng nhưng bottleneck chưa rõ

## Output / artifact nên có

- Metric/baseline rõ p95 latency, throughput, error rate hoặc resource usage
- Benchmark hoặc load test mô phỏng workload chính
- Decision note về bottleneck, threshold và trade-off cost/complexity

## Checklist kiểm tra

- Metric nào chứng minh vấn đề performance thật?
- Workload test có giống usage production không?
- Bottleneck nằm ở CPU, memory, I/O, database, network hay lock?
- Threshold pass/fail là bao nhiêu và ai chấp nhận?
- Tối ưu này làm tăng cost/complexity ở đâu?

## Lỗi / rủi ro thường gặp

- Benchmark không giống production nên kết luận sai
- Tối ưu sớm làm code phức tạp mà chưa giải bottleneck thật
- Cache/index/scale làm tăng cost hoặc inconsistency
- Không đo baseline nên không biết thay đổi có hiệu quả không

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần tối ưu sâu khi chưa có metric hoặc user impact
- Dễ over-engineer nếu scale architecture trước khi workload chứng minh cần

## Gồm những gì

- Chưa tách nhánh

## Liên quan

- [[Computer Performance]]

## Source trace

- Computer Networks Map / Ch01.4
