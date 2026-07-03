# Performance

Aliases: scalability, performance, hiệu năng

Type: Performance / Scalability

## Bản chất

Performance là vùng đo tốc độ, throughput, resource usage và khả năng chịu tải của hệ thống. Nó chỉ có ý nghĩa khi gắn với metric, workload và threshold cụ thể; nếu không có số đo thì rất dễ tối ưu nhầm chỗ.

## Dùng trong dự án để làm gì

Performance là MOC để đi tới các node phục vụ benchmark, profiling, bottleneck analysis, load test và capacity decision. Khi dự án có triệu chứng chậm hoặc chuẩn bị tăng tải, dùng trang này để chọn metric và cách đo trước khi tối ưu.

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

- [[Benchmark]]
- [[Profiling]]
- [[Bottleneck]]
- [[Cache]]
- [[Queue]]
- [[Load Test]]

## Liên quan

- Chưa liên kết thêm

## Source trace

- Data Intensive Applications Map
- Computer Organization Map
- SRE Map
